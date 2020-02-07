# Custom Setup on macOS

## Introduction

If you need more permanent solution than **HARDWARIO Playground** you can install all the services yourself in your system. This guide will help you to install and configure these services:

* HARDWARIO Gateway `bcg`
* HARDWARIO BigClown Firmware Tool `bcf`
* HARDWARIO Host Tool `bch`
* Mosquitto MQTT broker
* Node-RED
* The process manager `pm2`

## Playground Setup on Ubuntu

* open **Terminal** application

### **Step 1:**  Install the driver for the HARDWARIO **Radio Dongle**

* [Download & Install drivers from FTDI](http://www.ftdichip.com/Drivers/VCP/MacOSX/FTDIUSBSerialDriver_v2_4_2.dmg)

### Step 2: Restart your computer

### Step 3: Install [Homebrew](https://brew.sh/)

```text
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### **Step 4:** Upgrade all packages

```text
brew update && brew upgrade
```

###  **Step 5:** Install **Mosquitto** server and clients

```text
brew install mosquitto
```

```text
brew services start mosquitto
```

###  **Step 3:** Install **Node.js** version 6 \(required **by** **Node-RED**\)

```text
brew install node
```

###  **Step 4:** Install **Node-RED**

```text
sudo npm install -g --unsafe-perm node-red
```

###  **Step 5:**  Install **node-red-dashboard** for graphs, gauges, buttons

```text
cd ~/.node-red/
```

```text
npm i node-red-dashboard
```

### Step 7: Install PM2

```text
sudo npm install -g pm2
```

{% hint style="info" %}
**PM2** is a process manager that will help you to start **Node-RED** and other processes on boot.
{% endhint %}

### **Step 7:** Tell **PM2** to run **Node-RED**

```text
pm2 start `which node-red`
```

###  **Step 8:** Tell **PM2** to run on boot

```text
pm2 save
```

```text
pm2 startup
```

{% hint style="danger" %}
Now you must follow the instructions provided by the command `pm2 startup systemd`.
{% endhint %}

###  **Step 8:** Install **Python 3** \(required by the HARDWARIO **Firmware Tool** and HARDWARIO **Gateway**\)

```text
brew install python3
```

###  **Step 9:** Update **pip** \(Python Package Manager\) to the latest version

```text
sudo pip3 install --upgrade --no-cache-dir pip
```

###  **Step 10:** Install the HARDWARIO **Firmware Tool**

```text
sudo pip3 install --upgrade --no-cache-dir bcf
```

###  **Step 11:** Install the HARDWARIO **Gateway**

```text
sudo pip3 install --upgrade --no-cache-dir bcg
```

###  **Step 12:** Plug the HARDWARIO **Radio Dongle** into a USB port

###  **Step 13:** List the available devices

```text
bcf devices
```

{% hint style="info" %}
You can use `-v` parameter to see verbose information about the connected devices \(possibly helping you to identify them\).
{% endhint %}

###  Step 15: Upload the latest firmware into the HARDWARIO **Radio Dongle**:

```text
bcf update
```

```text
bcf flash bigclownlabs/bcf-gateway-usb-dongle:latest
```

### Step 16:  Start the HARDWARIO **Gateway** as **PM2** service:

```text
pm2 start `which python3` --name "bcg-ud" -- `which bcg` --device ...
```

{% hint style="info" %}
Replace `...` with the device listed using `bcf devices`.
{% endhint %}

{% hint style="warning" %}
If you want to update firmware in the **Radio Dongle**, first you have to stop **bcg** by the command `pm2 stop bcg-ud`. After update, restart the service by the command `pm2 restart bcg-ud`.
{% endhint %}

### Step 17:  Open your web browser with the URL:

* [http://localhost:1880/](http://localhost:1880/)

## Playground Upgrade on macOS

###  Upgrade all the packages

```text
brew update && brew upgrade
```

###  Upgrade **Node-RED**

```text
sudo npm update -g node-red
```

###  Upgrade **PM2**

```text
sudo npm update -g pm2
```

###  Upgrade the HARDWARIO **Firmware Tool**

```text
sudo pip3 install --upgrade --no-cache-dir bcf
```

###  Upgrade the HARDWARIO **Gateway**

```text
sudo pip3 install --upgrade --no-cache-dir bcg
```

