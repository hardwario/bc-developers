# Radio CO2 Monitor

This document will guide you through the **Radio CO2 Monitor** project. You will be able to see dashboard with CO2, temperature, humidity, ambient light and atmospheric pressure in **Node-RED** and view the data on your smart phone using the **Blynk** cloud and mobile app.

## Block Concept

![](../.gitbook/assets/_projects_radio-co2-monitor_block-diagram.svg)

## Requirements

* Either **BigClown Radio CO2 Monitor Kit**, or individual components:
  * 1x **BigClown Core Module**
  * 1x **BigClown Temperature Tag**
  * 1x **BigClown Humidity Tag**
  * 1x **BigClown Barometer Tag**
  * 1x **BigClown CO2 Module**
  * 1x **BigClown Battery Module**
  * 1x **BigClown Radio Dongle**
* One of these options:
  * **BigClown Playground** installed \(recommended\)

    You can find more information in the [**Quick Start Guide**](../basics/quick-start-guide.md) document.

  * **Raspberry Pi** with the **BigClown Raspbian** distribution

    You can find more information in the document [**Raspberry Pi Installation**](../tutorials/raspberry-pi-installation.md).

  * **BigClown Firmware Tool** installed

    You can find more information in the document [**Toolchain Setup**](../firmware/toolchain-setup.md).

## Firmware Upload

In this procedure we will use the **BigClown Playground** to upload firmware to the **Core Module**.

### Step 1: Connect the Micro USB cable to the **Core Module** and your computer.

### Step 2: Run the BigClown Playground

In the Firmware tab choose and upload the `bcf-radio-co2-monitor` firmware to the **Core Module**:

{% hint style="warning" %}
**Flashing Core Module R1 & R2**  
For differences of flashing older **Core Module 1** and newer **Core Module 2** please read **Core Module R1 and R2 comparison** in the **Hardware section**
{% endhint %}

### Step 3: Remove the Micro USB cable from the **Core Module** and your computer.

{% hint style="success" %}
At this point your firmware is successfully uploaded.
{% endhint %}

## Hardware Assembling

See short video with easy step by step demonstration:

{% embed url="https://youtu.be/jGxjl5v7kqE" %}

### Step 1: Start with the **Battery Module**.

{% hint style="warning" %}
Make sure the **Battery Module** does not have batteries inserted.
{% endhint %}

### Step 2: Plug the **CO2 Module** on top of the **Battery Module**.

### Step 3: Plug the **Core Module** on top of the **CO2 Module**.

### Step 4: Plug the **Temperature Tag** into a socket on the **CO2 Module**.

### Step 5: Plug the **Humidity Tag** into a socket on the **CO2 Module**.

### Step 6: Plug the **Barometer Tag** into a socket on the **CO2 Module**.

### Step 7: Plug the **Cover Module** on top of the **Core Module**.

## Playground Bootstrap

{% hint style="danger" %}
If you are using the new **BigClown Playground**, then use the **Functions** tab instead of using [**http://localhost:1880/**](http://localhost:1880/). Also the pairing process is now done in **Devices** tab. For communication test use the **Messages** tab.
{% endhint %}

### Step 1: Open **Node-RED** in your web browser:

[http://localhost:1880/](http://localhost:1880/)

### Step 2: You should see the empty workspace with **Flow 1:**

### **Step 3:** Insert the following snippet in the flow \(using **Menu &gt;&gt; Import**\) and click in **Flow 1** tab:

```text
[{"id":"2fc604fc.3b6abc","type":"inject","z":"dfc861b.b2a02a","name":"List all gateways","topic":"gateway/all/info/get","payload":"","payloadType":"str","repeat":"","crontab":"","once":false,"x":560,"y":460,"wires":[["a2c10833.24d5d8"]]},{"id":"1e4502b8.2f63fd","type":"inject","z":"dfc861b.b2a02a","name":"Start node pairing","topic":"gateway/usb-dongle/pairing-mode/start","payload":"","payloadType":"str","repeat":"","crontab":"","once":false,"x":570,"y":580,"wires":[["795ff5a7.8e266c"]]},{"id":"3d844ce2.932864","type":"inject","z":"dfc861b.b2a02a","name":"Stop node pairing","topic":"gateway/usb-dongle/pairing-mode/stop","payload":"","payloadType":"str","repeat":"","crontab":"","once":false,"x":560,"y":640,"wires":[["5967c452.c838bc"]]},{"id":"f202b253.2705b","type":"inject","z":"dfc861b.b2a02a","name":"List paired nodes","topic":"gateway/usb-dongle/nodes/get","payload":"","payloadType":"str","repeat":"","crontab":"","once":false,"x":560,"y":520,"wires":[["f0aca138.0b2c3"]]},{"id":"349f02fd.890f6e","type":"inject","z":"dfc861b.b2a02a","name":"Unpair all nodes","topic":"gateway/usb-dongle/nodes/purge","payload":"","payloadType":"str","repeat":"","crontab":"","once":false,"x":560,"y":700,"wires":[["2f1c5bb6.53d6f4"]]},{"id":"cf61d75d.4ad8f8","type":"mqtt in","z":"dfc861b.b2a02a","name":"","topic":"#","qos":"2","broker":"67b8de4a.029d3","x":530,"y":400,"wires":[["a5cb0658.f5d658"]]},{"id":"a5cb0658.f5d658","type":"debug","z":"dfc861b.b2a02a","name":"","active":true,"console":"false","complete":"false","x":790,"y":400,"wires":[]},{"id":"a2c10833.24d5d8","type":"mqtt out","z":"dfc861b.b2a02a","name":"","topic":"","qos":"","retain":"","broker":"717f7c18.ba0a24","x":770,"y":460,"wires":[]},{"id":"f0aca138.0b2c3","type":"mqtt out","z":"dfc861b.b2a02a","name":"","topic":"","qos":"","retain":"","broker":"717f7c18.ba0a24","x":770,"y":520,"wires":[]},{"id":"795ff5a7.8e266c","type":"mqtt out","z":"dfc861b.b2a02a","name":"","topic":"","qos":"","retain":"","broker":"717f7c18.ba0a24","x":770,"y":580,"wires":[]},{"id":"5967c452.c838bc","type":"mqtt out","z":"dfc861b.b2a02a","name":"","topic":"","qos":"","retain":"","broker":"717f7c18.ba0a24","x":770,"y":640,"wires":[]},{"id":"2f1c5bb6.53d6f4","type":"mqtt out","z":"dfc861b.b2a02a","name":"","topic":"","qos":"","retain":"","broker":"717f7c18.ba0a24","x":770,"y":700,"wires":[]},{"id":"67b8de4a.029d3","type":"mqtt-broker","z":"","broker":"127.0.0.1","port":"1883","clientid":"","usetls":false,"compatmode":true,"keepalive":"60","cleansession":true,"willTopic":"","willQos":"0","willPayload":"","birthTopic":"","birthQos":"0","birthPayload":""},{"id":"717f7c18.ba0a24","type":"mqtt-broker","z":"","broker":"127.0.0.1","port":"1883","clientid":"","usetls":false,"compatmode":true,"keepalive":"60","cleansession":true,"willTopic":"","willQos":"0","willPayload":"","birthTopic":"","birthQos":"0","birthPayload":""}]
```

It will look like this:

![](../.gitbook/assets/_projects_radio-co2-monitor_node-red-gw-controls.png)

This snippet provides control buttons for gateway/radio commands. These commands are sent over the MQTT protocol.

### Step 4: Deploy the flow using the **Deploy** button in the top-right corner:

### Step 5: Open the **debug** tab:

![](../.gitbook/assets/_projects_radio-co2-monitor_node-red-gw-debug.png)

{% hint style="info" %}
In the **debug** tab, you will be able to see all the MQTT messages.
{% endhint %}

### Step 6: Click on the **List all gateways** button. You should see a response like this in the **debug** tab:

![](../.gitbook/assets/_projects_radio-co2-monitor_node-red-gw-list.png)

{% hint style="success" %}
At this point, you've got working **Node-RED**, **MQTT**, **BigClown Radio Dongle**and **BigClown Gateway**.
{% endhint %}

## Radio Pairing



In this section, we will create a radio link between the **Radio Dongle** and the **Radio CO2 Monitor**.

Follow these steps in **Node-RED**:

### Step 1: Click on the **Start node pairing** button

![](../.gitbook/assets/_projects_radio-co2-monitor_node-red-gw-pair-start.png)

### Step 2: Insert the batteries into the **Radio CO2 Monitor** to send the pairing request \(you should also see the red LED on the **Core Module** to be on for about 2 seconds\).

### Step 3: Click on the **Stop node pairing** button.

![](../.gitbook/assets/_projects_radio-co2-monitor_node-red-gw-pair-stop.png)

{% hint style="success" %}
At this point, you've got established a radio link between the node \(**Radio Motion Detector**\) and the gateway \(**Radio Dongle**\).
{% endhint %}

## Communication Test

Follow these steps in **Node-RED**:

### Step 1: Switch to **debug** tab on the right

### Step 2: Test it

Start breathing on the temperature sensor on the **Temperature Tag** to invoke a change of temperature and hence trigger a radio transmission.

You should then see similar messages:

![](../.gitbook/assets/_projects_radio-co2-monitor_radio-test.png)

{% hint style="success" %}
At this point, you've got verified radio communication.
{% endhint %}

## Integration with Blynk

Now we have assembled our kit and let's start with some basic integration with **Blynk**. We will start without describing what **Blynk** is. If you want get some information about what **Blynk** is. The best thing you can do is to visit their [**page**](https://www.blynk.cc/). In our example we will be showing you how display values from your sensors in **Blynk**'s mobile application.

Firstly we need to configure our **Node-RED** app.

### Step 1: Blynk nodes

If you are using BigClown raspi version you should be fine, but still check that **Blynk** nodes are installed. \(You can view them on the left side menu in **Node-RED**\). Otherwise you will need to install **Node-RED** package `node-red-contrib-blynk-ws`.

![](../.gitbook/assets/_projects_radio-co2-monitor_integration-nodered-1.png)

### Step 2: Add another flow \(you can add them by big plus button next to the flow name\)

### Step 3: Insert the following snippet in the flow \(using **Menu &gt;&gt; Import**\) and click in Flow 3 tab

```text
[{"id":"31ab8ee9.420bb2","type":"mqtt in","z":"2c41a2bd.aa36ae","name":"","topic":"node/co2-monitor:0/thermometer/0:0/temperature","qos":"2","broker":"1292d7bf.db35a8","x":316,"y":483,"wires":[["cb15bc57.2b0a5"]]},{"id":"fa8f9692.6cb388","type":"mqtt in","z":"2c41a2bd.aa36ae","name":"","topic":"node/co2-monitor:0/hygrometer/0:4/relative-humidity","qos":"2","broker":"1292d7bf.db35a8","x":326,"y":543,"wires":[["dcea0ae2.3287b8"]]},{"id":"d9edba1c.71f348","type":"mqtt in","z":"2c41a2bd.aa36ae","name":"","topic":"node/co2-monitor:0/barometer/0:0/pressure","qos":"2","broker":"1292d7bf.db35a8","x":290,"y":600,"wires":[["31270a41.f16076"]]},{"id":"cb15bc57.2b0a5","type":"blynk-ws-out-write","z":"2c41a2bd.aa36ae","name":"","pin":"0","pinmode":0,"client":"90573d3c.a1cca","x":686,"y":483,"wires":[]},{"id":"f7853a1c.8891e8","type":"mqtt in","z":"2c41a2bd.aa36ae","name":"","topic":"node/co2-monitor:0/co2-meter/-/concentration","qos":"2","broker":"1292d7bf.db35a8","x":300,"y":660,"wires":[["39fede01.e9a5f2"]]},{"id":"dcea0ae2.3287b8","type":"blynk-ws-out-write","z":"2c41a2bd.aa36ae","name":"","pin":"1","pinmode":0,"client":"90573d3c.a1cca","x":686,"y":543,"wires":[]},{"id":"1b9b2c91.106d63","type":"blynk-ws-out-write","z":"2c41a2bd.aa36ae","name":"","pin":"2","pinmode":0,"client":"90573d3c.a1cca","x":680,"y":600,"wires":[]},{"id":"39fede01.e9a5f2","type":"blynk-ws-out-write","z":"2c41a2bd.aa36ae","name":"","pin":"3","pinmode":0,"client":"90573d3c.a1cca","x":680,"y":660,"wires":[]},{"id":"31270a41.f16076","type":"function","z":"2c41a2bd.aa36ae","name":"/ 1000","func":"msg.payload = msg.payload / 1000.0;\nreturn msg;","outputs":1,"noerr":0,"x":530,"y":600,"wires":[["1b9b2c91.106d63"]]},{"id":"1292d7bf.db35a8","type":"mqtt-broker","z":"","broker":"127.0.0.1","port":"1883","clientid":"","usetls":false,"compatmode":true,"keepalive":"60","cleansession":true,"willTopic":"","willQos":"0","willPayload":"","birthTopic":"","birthQos":"0","birthPayload":""},{"id":"90573d3c.a1cca","type":"blynk-ws-client","z":"","name":"","path":"ws://blynk-cloud.com/websockets","key":"","dbg_all":false,"dbg_read":false,"dbg_write":false,"dbg_notify":false,"dbg_mail":false,"dbg_prop":false,"dbg_low":false,"dbg_pins":""}]
```

It will look like this:

![](../.gitbook/assets/_projects_radio-co2-monitor_integration-nodered-2.png)

### Step 4: Connect

Configure MQTT node to connect it on you broker. It will propably connect on localhost if you are using Raspberry Pi. After that you will need to configure **Blynk** node. Just fill in URL `ws://blynk-cloud.com/websockets`. The `Auth Token` we will configure later after obtaining one from Blynk over e-mail.

![](../.gitbook/assets/_projects_radio-co2-monitor_integration-nodered-3.png)

### Step 5: Now download the **Blynk** app from [**App Store**](https://itunes.apple.com/us/app/blynk-iot-for-arduino-esp32/id808760481?mt=8) or [**Google Play**](https://play.google.com/store/apps/details?id=cc.blynk&hl=en)

### Step 6: After installing, you should create account, login and you should see something like that

![](../.gitbook/assets/_projects_radio-co2-monitor_integration-blynk-4.png)

### Step 7: Now click a button on the top right to scan QR code

![](../.gitbook/assets/_projects_radio-co2-monitor_integration-blynk-5.png)

### Step 8: Now you should scan following QR code to get everything preconfigured

![](../.gitbook/assets/_projects_radio-co2-monitor_integration-blynk-6.png)

### Step 9: You should see something like this

![](../.gitbook/assets/_projects_radio-co2-monitor_integration-blynk-7.png)

{% hint style="info" %}
You will see values after you launch your integration project.
{% endhint %}

### Step 10: Email

Click the settings wheel and you should see settings for your project. We need to get `Auth Token` which you have to copy to our **Node-RED** in **Blynk** node configuration.

![](../.gitbook/assets/_projects_radio-co2-monitor_integration-blynk-8.png)

### Step 11: Deploy

Now deploy your **Node-RED** app and hit play button in your **Blynk** project and you should be done!

### Related Documents <a id="related-documents"></a>

* [**Raspberry Pi Installation**](../tutorials/raspberry-pi-installation.md)
* [**Toolchain Setup**](../firmware/toolchain-setup.md)
* [**Toolchain Guide**](../firmware/toolchain-guide.md)

