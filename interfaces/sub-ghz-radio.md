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

* **Radio Dongle**

  You can pair up to 32 devices.

* **Radio Node**

  Every node has to be paired to the gateway. A node device can be some sensor \(e.g. temperature, humidity, CO2\) or actuator \(power relay, LCD display, LED strip controller\).

## Radio Pairing

Pairing process is very straightforward procedure:

### Step 1: The **gateway device** needs to be in the **pairing mode**

{% hint style="info" %}
The MQTT command for this operation is described in the document [**MQTT Topics**](mqtt-topics.md).
{% endhint %}

### **Step 2:** The **node device** has to transmit the **pairing request**

This is done by cycling the power on the **node device**. On battery-operated node, you simple remove the batteries, wait a few seconds \(to get the capacitors discharged\) and insert the batteries back. The pairing request is sent on the boot.

### **Step 3:** Once all **node devices** are enrolled, you have to exit the **pairing mode**

{% hint style="info" %}
The MQTT command for this operation is described in the document [**MQTT Topics**](mqtt-topics.md).
{% endhint %}

## Low Power Radio Communication

All battery operated radio nodes have turned off the radio receiver when they are sleeping. The gateway is listening all the time. This way it is very easy to send data anytime from battery operated node to the gateway.

The other way - communication from gateway to the remote node is a bit tricky. Let's say you would like battery operated node with Relay Module which is bistable and needs energy only when changing its state. There is few solutions for this functionality:

#### Using power adapter

By using Power Module or micro USB cable to power Core Module constantly you can enable in your firmware radion in listening mode [BC\_RADIO\_MODE\_NODE\_LISTENING](http://sdk.bigclown.com/group__bc__radio.html#gga8ea10987b9de5621bcf560019dd6f2b7a068d480094dcb86276069ed743c968a2).

#### Set listening timeout for sleeping node

In the firmware you can set the time that the sleeping node will listen after every send message from Node to the Gateway. You set it by calling [bc\_radio\_set\_rx\_timeout\_for\_sleeping\_node](http://sdk.bigclown.com/group__bc__radio.html#gga8ea10987b9de5621bcf560019dd6f2b7a068d480094dcb86276069ed743c968a2) API.

This way let's say you send the measured temperature every 10 minutes and in your Node-RED or server code you will react to this MQTT temperature message and immediatelly response with MQTT message to toggle the relay. We did some tests and 400 ms is more then enought timeout for Node-RED to send the response MQTT message.

This solution adds to the power consumption and you have to find right ballance between battery life and response time the relay can be switched.

#### Synchronized clock of nodes

With [RTC support in SDK](http://sdk.bigclown.com/group__bc__rtc.html) it is possible to synchronize the clock of the nodes and create a firmware that will for example listen for 1 second in every 10 minutes. This way the node does not need to send packet like in previous solution, but it needs to be perfectly time-synchronized with the gateway and Node-RED.

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

## Using 915 MHz for US, Canada & others

For parts of the world where the ISM band is 915 MHz, you cannot use default 868 MHz communication frequency. During the code compilation you have to pass `BAND` parameter to the `make` like this:

```text
make BAND=915
```

Right now it is not possible to use `bcf` tool because all the firmwares are pre-compiled with 868 MHz band. Make sure you also compile **Radio Dongle** firmware with this parameter.

## Packet Structure

| PRE\(4\) | SYN\(4\) | LEN\(1\) | DST\(1\) | DATA\(0..60\) | CRC\(2\) |
| :--- | :--- | :--- | :--- | :--- | :--- |


Explanation of the fields:

* **PRE\(4\)**

  This part is called **preamble** and consists of alternating sequence of zeroes and ones \(32 bits\).

* **SYN\(4\)**

  This part is called **synchronization word** and has a fixed value of `0x88888888`.

* **LEN\(1\)**

  This part determines the length of the `DATA` plus 1 \(`DST` field is also counted\).

* **DST\(1\)**

  This is destination address \(for logic network addressing\).

* **DATA\(0..60\)**

  Variable length payload data field.

* **CRC\(2\)**

  Checksum calculated over all fields excluding `PRE` and `SYN` fields. The polynomial of the CRC engine is `0x1021`.

## Related Documents

* [**SPIRIT1 Resources**](http://www.st.com/en/wireless-connectivity/spirit1.html)
* [**MQTT Protocol**](mqtt-protocol.md)
* [**MQTT Topics**](mqtt-topics.md)

