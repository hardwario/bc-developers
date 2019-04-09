# LoRa 1-Wire Thermometer

With this kit, you can measure **temperatures** with a single or multiple connected DS18B20 or DS18S20 temperature sensors. Then the values are sent wirelessly to the LoRa gateway.

You can use community The Things Network to receive the data.

## What You Will Need

* [Core Module](https://shop.bigclown.com/core-module)
* [LoRa Module](https://shop.bigclown.com/lora-module)
* [Mini Battery Module](https://shop.bigclown.com/mini-battery-module)
* [Sensor Module](https://shop.bigclown.com/sensor-module)
* [DS18B20 Temperature Sensor](https://shop.bigclown.com/ds18b20-temperature-sensor/)

## Firmware Upload

### Step 1: Download the latest [**BigClown Playground**](https://github.com/bigclownlabs/bch-playground/releases/latest)

### Step 2: Connect the Core Module to your computer.

### Step 3: In Playground, go to the **Firmware** tab, select `bcf-lora-1wire-thermometer`and flash the firmware.

### Step 4: After upload, the red LED on the Core Module will turn on for 2 seconds, then it will turn off.

## LoRa Configuration

For configuring the LoRa keys please follow [LoRa AT Commands Configuration](https://www.bigclown.com/doc/tutorials/lora-at-commands-configuration/) tutorial.

## Transmitting the data

The LoRa Climate Monitor sends a LoRa packet when:

* After power-up, when the batteries are inserted
* Every 15 minutes when the measure values are the same
* After pressing the button
* When you type `AT$SEND` to the console

## Reading the Data

The data are encoded in the LoRa message. You need to extract the right bits to get the values back. This is explained in the [README.md](https://github.com/bigclownlabs/bcf-lora-climate-monitor/blob/master/README.md#buffer) file. You can also use the `decode.py`python [script in the repository](https://github.com/bigclownlabs/bcf-lora-climate-monitor).

You can pass the received HEX string as a parameter for the `decode.py`:

```text
>>> python3 decode.py 001D00E600E8012200E500D600E5

Header : BOOT
Voltage : 2.9
Sensor  0 : 23.0
Sensor  1 : 23.2
Sensor  2 : 29.0
Sensor  3 : 22.9
Sensor  4 : 21.4
Sensor  5 : 22.9
```

