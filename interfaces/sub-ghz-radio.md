# Sub-GHz Radio

The radio communication technology is the heart of the **BigClown IoT Kit**. This document describes the basic operation of the radio.

With **BigClown**, you can build your own network in the Sub-GHz band.

The radio frequency **868 MHz** \(for Europe\) or **915 MHz** \(for the U.S.\) allows long distance communication and offers low-power operation. Since this frequency band is used for signal messages, you will not encounter interference with streaming protocols like WiFi, Bluetooth, etc.

{% hint style="info" %}
BigClown uses **SPIRIT1** radio transceiver from **STMicroelectronics**.
{% endhint %}

![SPIRIT1](../.gitbook/assets/_interfaces_sub-ghz-radio_spirit1.jpg)

## Communication Range

We have done several radio communication tests. We claim, that from a single point, you are typically able to provide a full-house radio coverage.

On the other hand, several factors influence the communication distance - the most important is the building material from which you have built your house, obstacles in the path, interference from other appliances, etc.

The only objective radio communication range measurement is a so-called **line-of-sight**distance measured outdoor.

{% hint style="success" %}
We've achieved [more than 500 meters line-of-sight](https://youtu.be/6zdQQdwV3GQ) communication range between two **Core Modules**.

Also the single Radio Dongle / Core Module is enough to [cover three-story house and whole garden around it](https://youtu.be/JplQxCYSClA).
{% endhint %}

On the other hand, if the radio communication range is not sufficient, the network can be expanded on IP level thanks to MQTT message replication to a master server.

{% hint style="info" %}
You will need to search for `connection`, `address` and `topic` directives in the `mosquitto.conf` configuration file.
{% endhint %}

## Radio Topology

**BigClown** supports only **star network topology**. Such configuration offers high reliability, easy troubleshooting and deterministic service time from batteries.

There are two types of devices in the **BigClown** radio network:

* **Gateway Device**

  There can be only one gateway device per network. The gateway device can be either:

  * BigClown **Radio Dongle** \(it can handle up to **32 devices**\)
  * BigClown **Core Module** \(it can handle up to **16 devices**\)

* **Node Device**

  There can be one to several node devices in the network. Every node has to be paired to the gateway. A node device can be some sensor \(e.g. temperature, humidity, CO2\) or actuator \(power relay, LCD display, LED strip controller\).

## Radio Pairing

Pairing process is very straightforward procedure:

### Step 1: The **gateway device** needs to be in the **pairing mode**

{% hint style="info" %}
The MQTT command for this operation is described in the document [**MQTT Topics**](https://www.bigclown.com/doc/interfaces/mqtt-topics/).
{% endhint %}

### **Step 2:** The **node device** has to transmit the **pairing request**

This is done by cycling the power on the **node device**. On battery-operated node, you simple remove the batteries, wait a few seconds \(to get the capacitors discharged\) and insert the batteries back. The pairing request is sent on the boot.

### **Step 3:** Once all **node devices** are enrolled, you have to exit the **pairing mode**

{% hint style="info" %}
The MQTT command for this operation is described in the document [**MQTT Topics**](https://www.bigclown.com/doc/interfaces/mqtt-topics/).
{% endhint %}

## Radio Parameters

| **Parameter** | Value |
| :--- | :--- |
| Communication frequency \(Europe\) | 868.0 MHz |
| Communication frequency \(U.S.\) | 915.0 MHz |
| Modulation Type | GFSK |
| Modulation Rate | 19.2 kbps |
| TX Frequency Deviation | 20 kHz |
| TX Transmit Power | 11.6 dBm |
| RX Filter Bandwidth | 100 kHz |

