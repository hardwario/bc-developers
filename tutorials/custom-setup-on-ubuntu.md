# Custom Setup on Ubuntu

## Introduction

If you need more permanent solution than **BigClown Playground** you can install all the services yourself in your system. This guide will help you to install and configure these services:

* BigClown Gateway `bcg`
* BigClown Firmware Tool `bcf`
* BigClown Host Tool `bch`
* Mosquitto MQTT broker
* Node-RED
* The process manager `pm2`

## Playground Setup on Ubuntu

* open **Terminal** application

### **Step 1:** Upgrade all packages

```text
sudo apt update && sudo apt upgrade
```

###  **Step 2:** Install **Mosquitto** server and clients

```text
sudo apt install mosquitto mosquitto-clients
```

###  **Step 3:** Install **Node.js** version 6 \(required **by** **Node-RED**\)

```text
sudo apt install nodejs nodejs-legacy npm
```

###  **Step 4:** Install **Node-RED**

```text
sudo npm install -g --unsafe-perm node-red
```

###  **Step 5:** Install **node-red-dashboard** for graphs, gauges, buttons

```text
sudo npm install -g pm2
```

###  **Step 6:** Tell **PM2** to run **Node-RED**

```text
pm2 start `which node-red`
```

###  **Step 7:** Tell **PM2** to run on boot

```text
pm2 save
```

```text
pm2 startup systemd
```

{% hint style="danger" %}
Now you must follow the instructions provided by the command `pm2 startup systemd`.
{% endhint %}

###  **Step 8:** Install **Python 3** \(required by the **BigClown Firmware Tool** and **BigClown Gateway**\)

```text
sudo apt install python3.5 python3-pip
```

###  **Step 9:** Update **pip** \(Python Package Manager\) to the latest version

```text
sudo pip3 install --upgrade --no-cache-dir pip
```

###  **Step 10:** Install the **BigClown Firmware Tool**

```text
sudo pip3 install --upgrade --no-cache-dir bcf
```

###  **Step 11:** Install the **BigClown Gateway**

```text
sudo pip3 install --upgrade --no-cache-dir bcg
```

###  **Step 12:** Add yourself to the **dialout** user group

```text
sudo usermod $USER -a -G dialout
```

###  **Step 13:** Plug the **BigClown Radio Dongle** into a USB port

###  **Step 14:** List the available devices

```text
bcf devices
```

{% hint style="info" %}
You can use `-v` parameter to see verbose information about the connected devices \(possibly helping you to identify them\).
{% endhint %}

###  Step 15: Upload the latest firmware into the **BigClown Radio Dongle**:

```text
bcf update
```

```text
bcf flash bigclownlabs/bcf-gateway-usb-dongle:latest
```

### Step 16:  Start the **BigClown Gateway** as **PM2** service:

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

## Playground Upgrade on Ubuntu

###  Upgrade all the packages

```text
sudo apt update && sudo apt upgrade
```

###  Upgrade **Node-RED**

```text
sudo npm update -g node-red
```

###  Upgrade **PM2**

```text
sudo npm update -g pm2
```

###  Upgrade the **BigClown Firmware Tool**

```text
sudo pip3 install --upgrade --no-cache-dir bcf
```

###  Upgrade the **BigClown Gateway**

```text
sudo pip3 install --upgrade --no-cache-dir bcg
```

