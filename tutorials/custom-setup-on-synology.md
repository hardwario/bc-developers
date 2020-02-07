# Custom Setup on Synology

You can have HARDWARIO Gateway running on Raspberry Pi, but if you have any kind of NAS already running 24/7 in your newtwork, why not take advantage of it? You will save a tiny bit on electricity bill and also get more durable system.

![](../.gitbook/assets/_tutorials_custom-setup-on-synology_synology-bigclown.jpg)



If you need more permanent solution than **HARDWARIO Playground** you can install all the services yourself in your system. This guide will help you to install and configure these services:

* HARDWARIO Gateway `bcg`
* HARDWARIO Firmware Tool `bcf`
* HARDWARIO Host Tool `bch`
* Mosquitto MQTT broker
* Node-RED
* The process manager `pm2`

## About project <a id="about-project"></a>

Synology NAS is a very versatile device. You can install many services with a single click of your mouse. You can also SSH to the internal Linux OS and change anything you like. If you connect [Radio Dongle](https://shop.bigclown.com/radio-dongle) it appears as `/dev/ttyUSB0` so it's easy to use Synology NAS as a HARDWARIO gateway. You can install `Python`, HARDWARIO gateway `bcg` and `mosquitto`very easily. You can also use **Docker** to run different services separately from the host OS.

{% hint style="info" %}
**Virtalization which is used in this tutorial is not necessary**. You can install MQTT broker, Python 3 and `bcg` gateway directly on Linux which already runs on your NAS of any brand. The virtualization step is optional and it was choosed because my NAS supported it and has plenty of resources. On Synology just SSH to the NAS IP and use your name and password which you use to login to the web management.
{% endhint %}

This tutorial is **going further** and is using the **Virtual Machine Manager** to create completely separate virtual Ubuntu 16.04 server. Please see the [list of supported Synology NAS](https://www.synology.com/en-global/dsm/packages/Virtualization).

All the services will be installed inside the virtual machine. The advantage is that this machine can be easily exported and moved to another host. Synology is using QEMU emulator, but exported machines can be run also in Virtualbox without any issue. Other advantage is that you get more robustness of your data in comparison of Raspberry Pi which is using microSD card. Synology can use BTRFS filesystem which is immune to failure of one or many hard drives.

## Installation <a id="installation"></a>

### Step 1: Install [Virtual Machine Manager](https://www.synology.com/en-global/dsm/packages/Virtualization)

![](../.gitbook/assets/_tutorials_custom-setup-on-synology_vmm-install.png)

### Step 2: Download latest [Ubuntu Server](https://www.ubuntu.com/download/server). The 64 bit is important because Grafana do not release 32 bit versions anymore.

### Step 3: Open **Virtual Machine Manager** and create a new virtual machine. The parameters below are the minimal which were tested

* **Generic** tab
  * **1 CPU Core**
  * **1 GB of RAM**
* **Storage** tab
  * **Boot ISO file** - select your downloaded installation ISO
  * **Virtual disk size** - 10 GB
* **Other** tab
  * **Virtual USB driver** - USB 2.0 or 3.0 \(**you can change this only when a virtual machine is turned off**\)
  * **USB Device** - select the Radio Dongle which is connected to you Synology NAS now, or later after you install virtual machine.

### Step 4: Confirm virtual machine creation, turn on the virtual machine and press **Connect**so noVNC virtual console is opened in your browser, follow the installation steps to install the Ubuntu.

### Step 5: If you did not already inserted [Radio Dongle](https://shop.bigclown.com/radio-dongle), do it now. Open virtual machine configuration on the **Other** tab and in the **USB device** list select **Future Technology Devices International**.

{% hint style="warning" %}
If you disconnect **Radio Dongle** from the USB then this **USB device** configuration **must be set again!**
{% endhint %}

![](../.gitbook/assets/_tutorials_custom-setup-on-synology_vmm-usb.png)

### Step 6: Follow steps [Custom Setup on Ubuntu](custom-setup-on-ubuntu.md) to install all the tools and services.

### Step 7: Now you have Node-RED, Grafana and all the tools running on your Synology NAS.

![](../.gitbook/assets/_tutorials_custom-setup-on-synology_grafana.png)

![](../.gitbook/assets/_tutorials_custom-setup-on-synology_node-red.png)

