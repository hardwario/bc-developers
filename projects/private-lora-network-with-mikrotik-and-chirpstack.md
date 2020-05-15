# Private LoRa network with Mikrotik & ChirpStack

This tutorial explains how to set-up private LoRaWAN network with Mikrotik wAP LR8 kit and ChirpStack running on any Linux computer.

## Mikrotik wAP LR9 kit quick start

Connect to your Mikrotik with instructions on official [wAP LR8 kit page](https://help.mikrotik.com/docs/display/UM/wAP+LR8+kit). First connection is over the WiFi only. We change that later.

{% hint style="info" %}
In case you would need to factory reset Mikrotik, [follow these instructions](https://wiki.mikrotik.com/wiki/Manual:Reset). Just make sure you follow the right green LED which is the WiFi LED under the power barrel jack.

Inside the unit on LoRa card is another green LED which is blinking after start and it is bit confusing. Do not follow that green LED inside unit.
{% endhint %}

## Enable ethernet interface connection/disable WLAN

Optional. By default the firewall is set that you cannot connect to RouterOS configuration over ethernet. You enable that by disabling all rules in Firewall. Go to IP &gt; Firewall and disable all the rules by clicking on the "D" button next to them.

Ethernet should now work and lease a DHCP address. Now you could connect to the RouterOS over ethernet.

You can also optionally completely disable WLAN. You do that in Interfaces where you disable "wlan1".

## Enable LoRa

LoRa is disabled by default. Enable it in LoRa menu and press "E" to enable it. In the traffic tab you should see incoming packets. They are encrypted so you can see correctly just Dev Addr, but it is quite useful to see the hardware is working correctly.

## Install ChirpStack

In this part you install **ChirpStack Gateway Bridge, ChirpStack Network Server, ChirpStack Application Server** to your Linux server. Your Mikrotik wAP LR9 will then later connect to this server and will forward LoRa packets there.

For Debian you can follow [Debian/Ubuntu install tutorial](https://www.chirpstack.io/guides/debian-ubuntu/), otherwise see this [generic installation page](https://www.chirpstack.io/install/install/).

{% hint style="info" %}
In the Debian/Ubuntu installation tutorial there is a Postgress table creation script. You can copy complete script and paste it into the Posgress console. After table creation you just press enter and that executes the last command to exit the prompt.
{% endhint %}

## Connect to Network Server

{% hint style="info" %}
Do no forget to enable to open port 8080 in your server firewall for Chirp web page and 1700 for the Gateway Bridge. Also if you use MQTT open port 1883. If you use `ufw` then type `sudo ufw allow 8080`.
{% endhint %}

Follow instructions [how to connect to ChirpStack Application Server](https://www.chirpstack.io/guides/first-gateway-device/).

## Connect Mikrotik gateway to ChirpStack

Open the LoRa menu on the Mikrotik configuration. In previous step we've enabled LoRa hardware. Now it's time to set up the ChirpStack Gateway Server IP. Go to LoRa &gt; Servers and set the IP of your server and both ports to 1700.

The second step is to go to Devices, open gateway detail and in Network Servers you have to choose the added network server. It may be needed to disable LoRa temporarily to change this settings.

You also should set Network type to Private. Then also you need to set private configuration to all your LoRaWAN nodes.

In the left menu in Log you should see "Forwarder started" text 

{% hint style="info" %}
On your server you can run `sudo journalctl -f -n 100 -u chirpstack-gateway-bridge.service` and see the logs of incoming messages to make sure the connection is set up correctly.
{% endhint %}

## Set gateway and devices to ChirpStack

Then follow [these steps in ChirpStack tutorial](https://www.chirpstack.io/guides/first-gateway-device/) to add your network-server, gateway, organization and profiles as explained



|  |
| :--- |


