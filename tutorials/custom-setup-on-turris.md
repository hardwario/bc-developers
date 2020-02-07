# Custom Setup on Turris

If you need more permanent solution than **HARDWARIO Playground** you can install all the services yourself in your system. This guide will help you to install and configure these services:

* HARDWARIO Gateway `bcg`
* HARDWARIO Firmware Tool `bcf`
* HARDWARIO Host Tool `bch`
* Mosquitto MQTT broker
* Node-RED
* The process manager `pm2`

## Installation

### Step 1: Update the package

```text
opkg update
```

### Step 2: Install the driver for the HARDWARIO **Radio Dongle** and HARDWARIO **Core module**:

```text
opkg install kmod-usb-serial-ftdi kmod-usb-acm
insmod ftdi_sio
insmod cdc_acm
```

### Step 3: Install [**Mosquitto**](https://mosquitto.org/) server and clients:

```text
opkg install mosquitto mosquitto-client
```

### Step 4: Enable service for [**Mosquitto**](https://mosquitto.org/)

```text
/etc/init.d/mosquitto enable
```

### Step 5: Start [**Mosquitto**](https://mosquitto.org/) service

```text
/etc/init.d/mosquitto start
```

### Step 6: Install **Python 3** \(required by the HARDWARIO **Gateway** and HARDWARIO **Firmware Tool**\)

```text
opkg install python3 python3-pip
```

### Step 7: Install the HARDWARIO **Gateway**, HARDWARIO **Flash Tool** and HARDWARIO **Host Tool**

```text
pip3 install --upgrade --no-cache-dir bcg
```

```text
pip3 install --upgrade --no-cache-dir bcf
```

```text
pip3 install --upgrade --no-cache-dir bch
```

## Finishing for Radio Dongle as a gateway

Follow these steps if you have [Radio Dongle](https://shop.bigclown.com/radio-dongle) as a gateway.

### Step 1: Finish [installation](custom-setup-on-turris.md#installation) part

### Step 2: Download configuration

```text
wget "https://raw.githubusercontent.com/bigclownlabs/bch-gateway/master/turris/etc/config/bc-gateway-usb-dongle" -O /etc/config/bc-gateway-usb-dongle
```

### Step 3: Make sure the configuration works

```text
uci show bc-gateway-usb-dongle
```

### Step 4: Download Init Script

```text
wget "https://raw.githubusercontent.com/bigclownlabs/bch-gateway/master/turris/etc/init.d/bc-gateway-usb-dongle" -O /etc/init.d/bc-gateway-usb-dongle
```

### Step 5: Add execute permission

```text
chmod u+x /etc/init.d/bc-gateway-usb-dongle
```

### Step 6: Enable service for gateway

```text
/etc/init.d/bc-gateway-usb-dongle enable
```

### Step 7: Start service

```text
/etc/init.d/bc-gateway-usb-dongle start
```

