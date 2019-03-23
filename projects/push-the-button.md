# Push The Button

**Push Button Kit** can interact with your world. Get phone notification, play next Spotify song, control your smart lights, trigger the egg timer or send a Tweet to the world.

In this tutorial you create a simple project with a button, that sends you push notification to your phone everytime you press it.

| ![](../.gitbook/assets/_projects_push-the-button_button-garage.jpg) | ![](../.gitbook/assets/_projects_push-the-button_button-dining-table.jpg) |
| :--- | :--- |


## Build Hardware

You will need the [Push Button Kit](https://shop.bigclown.com/push-button-kit) and [Radio Dongle](https://shop.bigclown.com/radio-dongle).

### Step 1: Assembly

Put all three modules together to build the **Push Button Kit**. Note the orientation of the Mini Battery Module on the image below.

![](../.gitbook/assets/_projects_push-the-button_mini-battery-module-orientation.png)

### Step 2: Put the batteries in

{% hint style="info" %}
The red LED on the Core Module will light up for 2 seconds when the batteries are inserted. This way you know that batteries are fine and kit is running ok.
{% endhint %}

## Playground Set-Up

In this step you run the **Playground** application that manages Radio Dongle, Push Button and thanks to the **Node-RED** connects everything together.

### Step 1: Download and run the latest [**BigClown Playground**](https://github.com/bigclownlabs/bch-playground/releases/latest)

![](../.gitbook/assets/_projects_push-the-button_playground-logo.png)

### **Step 2:** Connect [Radio Dongle](https://shop.bigclown.com/radio-dongle) to your computer

![](../.gitbook/assets/_projects_push-the-button_connect-usb-dongle.png)

### Step 3: Go to the **Devices** tab, check that the Radio Dongle is detected and click **Connect**

{% hint style="info" %}
If you cannot see Radio Dongle in the devices, please see the [Troubleshooting](https://www.bigclown.com/doc/projects/push-the-button/#troubleshooting) chapter.
{% endhint %}

![](../.gitbook/assets/_projects_push-the-button_playground-devices-connect.png)

### **Step 4:** When connected. The already flashed and paired Push Button Kit will be in the paired devices

![](../.gitbook/assets/_projects_push-the-button_playground-devices-connected.png)

### Step 5: Switch to the **Functions** tab and make sure you see the flow on the image below

![](../.gitbook/assets/_projects_push-the-button_node-red-flow.png)

In case you don't see the flow, you can copy the text below and paste it into the Node-RED's Menu &gt; Import &gt; Clipboard

```text
[{"id":"103c675c.c81139","type":"mqtt in","z":"2c41a2bd.aa36ae","name":"","topic":"node/push-button:0/push-button/-/event-count","qos":"2","broker":"29fba84a.b2af58","x":270,"y":360,"wires":[["ff41c7e0.06eba8"]]},{"id":"f507ecc3.8f82b","type":"blynk-ws-out-notify","z":"2c41a2bd.aa36ae","name":"Blynk notification","client":"fc4bbabb.9bb1b8","queue":false,"rate":5,"x":790,"y":360,"wires":[]},{"id":"ff41c7e0.06eba8","type":"change","z":"2c41a2bd.aa36ae","name":"Set message","rules":[{"t":"set","p":"payload","pt":"msg","to":"Button pressed, you're the best!","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":570,"y":360,"wires":[["f507ecc3.8f82b"]]},{"id":"c131dd35.bb855","type":"comment","z":"2c41a2bd.aa36ae","name":"Push Button Kit flow","info":"","x":190,"y":300,"wires":[]},{"id":"29fba84a.b2af58","type":"mqtt-broker","z":"","broker":"127.0.0.1","port":"1883","clientid":"","usetls":false,"compatmode":true,"keepalive":"60","cleansession":true,"birthTopic":"","birthQos":"0","birthPayload":"","willTopic":"","willQos":"0","willPayload":""},{"id":"fc4bbabb.9bb1b8","type":"blynk-ws-client","z":"","name":"","path":"ws://blynk-cloud.com/websockets","key":"5cf554e34caf4d49a1b24cd07c5e2c13","dbg_all":false,"dbg_read":false,"dbg_write":false,"dbg_notify":false,"dbg_mail":false,"dbg_prop":false,"dbg_sync":false,"dbg_bridge":false,"dbg_low":false,"dbg_pins":"","multi_cmd":false,"proxy_type":"no","proxy_url":""}]
```

## Blynk Mobile App Set-Up

In this step you configure **Blynk** application on your phone so you can get notifications from the **BigClown Playground**.

### Step 1: Download Blynk

Now download the **Blynk** app from [**App Store**](https://itunes.apple.com/us/app/blynk-iot-for-arduino-esp32/id808760481?mt=8) or [**Google Play**](https://play.google.com/store/apps/details?id=cc.blynk&hl=en). Create an account and log-in.

### Step 2: Click on the **QR icon**

![](../.gitbook/assets/_projects_push-the-button_blynk-copy.png)

### **Step 3:** Scan following QR code to get everything preconfigured

![](../.gitbook/assets/_projects_push-the-button_blynk-qr-code-push.button-kit.png)

### Steo 4: You will see this imported **project** with a single **Notification Widget**

Click on the **Settings icon**.

![](../.gitbook/assets/_projects_push-the-button_blynk-config.png)

### **Step 5:** Scroll down and click on **Email all** tokens. We use this token from you email later

![](../.gitbook/assets/_projects_push-the-button_blynk-token.png)

### Step 6: Now you need start the Blynk project. Click on the **Play** symbol

![](../.gitbook/assets/_projects_push-the-button_blynk-play.png)

## Putting it all together

The final step is to connect Node-RED and Blynk together, so you can get the notifications.

### Step 1: In the **Playground** **Functions** tab doubleclick on the **Blynk notification** node

### Step 2: Click on the **pencil icon** and paste the token you've received in the email. Click **Done**

### **Step 3:** Click the **Deploy** button. Everytime you edit the Node-RED flow you have to apply changes!

![](../.gitbook/assets/_projects_push-the-button_node-red-token.png)

## Action !

The time has come to **PUSH THE BUTTON**

| ![](../.gitbook/assets/_projects_push-the-button_push-the-button.png) | ![](../.gitbook/assets/_projects_push-the-button_button-pressed.png) |
| :--- | :--- |


## Learn More

The goal of this **Push Button Project** is to show the basics in a few simple steps. Now you can learn more by browsing the **documentation** or by visiting the **links below**.

* Check out other BigClown [**projects**](projects-overview.md).
* Take a look at the [**Module Overview**](../basics/module-overview.md).
* Learn about [**MQTT**](../interfaces/mqtt-protocol.md) and [**BigClown MQTT topics**](../interfaces/mqtt-topics.md) to control LEDs and relays.
* Try other [**integrations**](../integrations/grafana-for-visualization.md) with **Grafana**, **Blynk**, **IFTTT**, **Ubidots** and others.
* Use your [**Raspberry PI**](../tutorials/raspberry-pi-installation.md) or other [**single board computer \(SBC\)**](../tutorials/custom-setup-on-raspberry-pi.md#setup-on-original-raspbian) as a server.
* [**Flash other firmware**](https://www.bigclown.com/doc/projects/radio-door-sensor/#flash-door-sensor-firmware.en.md) or [**write your own firmware**](../firmware/basic-overview.md) for the **Core Module**.
* Check the [**Core Module pinouts**](../hardware/header-pinout.md) and add your own buttons, relays and sensors.

