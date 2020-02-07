# Raspberry Pi Installation

## Introduction

{% hint style="warning" %}
If you already have Raspberry Pi with the original Raspbian distribution, go to the section [**Setup on Original Raspbian**](custom-setup-on-raspberry-pi.md#setup-on-original-raspbian). Or if you have OSMC, go to section [**Setup on OSMC**](raspberry-pi-installation.md#instructions-for-installing)
{% endhint %}

This document will guide you through installing Raspberry Pi. The tutorial is tested for Raspberry Pi 3 \(Model B\) but should also work for older Raspberry Pi 2.

{% hint style="info" %}
Raspberry Pi is a small, affordable, single-board computer that is able to run Linux operating system. BigClown uses this system to process sensor information, actuator control, decision logic for automation, data storage, or serve as a gateway to connect cloud services.
{% endhint %}

In the following procedure, we will install the **HARDWARIO Raspbian** Linux distribution. Raspbian is the official and most widely distributed Linux distribution for Raspberry Pi. BigClown maintains a modified version of this distribution that facilitates some steps and includes pre-installed packages that are key to HARDWARIO.

## Requirements

* Raspberry Pi 3 \(Model B\)
* MicroSD card with a minimum capacity of 4 GB
* MicroSD Card Reader \(+ optional SD Card Adapter\)
* Ethernet cable
* Workstation or laptop
* Router \(or LAN switch\) with the DHCP server set up
* One of the following operating systems:
  * Windows 7, 8.x, 10 \(32-bit or 64-bit\)
  * macOS \(tested on version 10.12.x\)
  * Ubuntu \(tested on version 18.04.2 LTS\)

## Instructions for Installing

### Download

* [HARDWARIO Raspian](https://github.com/bigclownlabs/bc-raspbian/releases)
* [balenaEtcher](https://www.balena.io/etcher/)

### Flash

1. Insert microSD card to reader in you computer
2. Open balenaEtcher you've downloaded
3. Select Bigclown Raspian which you also downloaded
4. Select insered SD card
5. Click flash
6. After flash insert microSD card to Raspberry Pi, connect microUSB power adapter and Ethernet cable or use Wifi setup in next chapter

## WiFi Setup \(optional\)

If you would not like to use ethernet cable, you can connect Raspberry Pi over your WiFi

1. Connect microSD card with HARDWARIO Raspbian to computer
2. Open boot section in your file explorer or Finder
3. Create file **wpa\_supplicant.conf**
4. Edit file with next text, then save and insert microSD card back to Raspberry Pi:

```text
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="YOUR_NETWORK_NAME"
    psk="YOUR_PASSWORD"
}
```



