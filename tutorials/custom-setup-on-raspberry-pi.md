# Custom Setup on Raspberry Pi

If you need more permanent solution than **HARDWARIO Playground** you can install all the services yourself in your system. This guide will help you to install and configure these services:

* HARDWARIO Gateway `bcg`
* HARDWARIO Firmware Tool `bcf`
* HARDWARIO Host Tool `bch`
* Mosquitto MQTT broker
* Node-RED
* The process manager `pm2`

## Differences from the Original Raspbian

This is a brief list of differences:

* Hostname is `hub` instead of `raspberrypi`.
* The time zone is set to `Europe/Prague`.
* The following records were added to the repository APT list:
  * [https://deb.nodesource.com/node\_8.x](https://deb.nodesource.com/node_8.x)
  * [http://repo.mosquitto.org/debian](http://repo.mosquitto.org/debian)
* By default, these packages are also installed:
  * mosquitto
  * mosquitto-clients
  * nodejs
  * python3-pip
  * python3-venv
  * dfu-util
  * git
  * htop
  * mc
  * tmux
  * npm pm2
  * npm node-red
  * pip3 bcf
  * pip3 bcg

## Setup on Original Raspbian

{% hint style="warning" %}
Apply the following procedure only if you are using Raspberry Pi, on which the original Raspbian distribution is running. This is an alternative way of installing `bc-raspbian` in \[\]\(/doc/tutorials/raspberry-pi-installation/\).
{% endhint %}

### Step 1: Log in to the Raspberry Pi using SSH. Detailed procedure is provided in the document [**Raspberry Pi Login**](raspberry-pi-login.md)

### Step 2: Upgrade all packages

```text
sudo apt update && sudo apt upgrade
```

### Step 3: Install **Mosquitto** server and clients

```text
sudo apt install mosquitto mosquitto-clients
```

### Step 4: Install **Node.js** version 8 \(required by **Node-RED**\)

```text
curl -sL  https://deb.nodesource.com/setup_8.x | sudo -E bash -
```

```text
sudo apt-get install -y nodejs
```

### Step 5: Install **Node-RED**

```text
sudo npm install -g --unsafe-perm node-red
```

### **Step 6:** Install **PM2**

```text
sudo npm install -g pm2
```

### **Step 7:** Tell **PM2** to run **Node-RED**

Make sure you copy next command exactly with the back-tick symbol \`.

```text
pm2 start `which node-red` -- --verbose
```

```text
pm2 save
```

### **Step 8:** Tell **PM2** to run on boot

```text
sudo -H PM2_HOME=/home/$(whoami)/.pm2 pm2 startup systemd -u $(whoami)
```

```text
sudo -H chmod 644 /etc/systemd/system/pm2-$(whoami).service
```

### Step 9: Install **Python 3** \(required by the HARDWARIO **Firmware Tool** and HARDWARIO **Gateway**\)

```text
sudo apt install python3 python3-pip python3-setuptools
```

### Step 10: Update **pip** \(Python Package Manager\) to the latest version

```text
sudo pip3 install --upgrade pip
```

### Step 11: Install the HARDWARIO **Firmware Tools**

BigClown Firmware Tool `bcf`, HARDWARIO Gateway `bcg` and HARDWARIO Host Tool `bch`.

```text
sudo pip3 install --upgrade bcf bcg bch
```

### **Step 12:** Add udev rules

```text
echo 'SUBSYSTEMS=="usb", ACTION=="add", KERNEL=="ttyUSB*", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6015", ATTRS{serial}=="bc-usb-dongle*", SYMLINK+="bcUD%n", TAG+="systemd", ENV{SYSTEMD_ALIAS}="/dev/bcUD%n"'  | sudo tee --append /etc/udev/rules.d/58-bigclown-usb-dongle.rules
```

{% hint style="warning" %}
Unplug and plug gateway.
{% endhint %}

### Step 13: Run service for Gateway Radio Dongle

```text
pm2 start /usr/bin/python3 --name "bcg-ud" -- /usr/local/bin/bcg --device /dev/bcUD0
```

```text
pm2 save
```

