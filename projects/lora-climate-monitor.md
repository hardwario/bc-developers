# LoRa Climate Monitor

With this kit, you can measure **temperature**, **humidity**, **luminosity** and **pressure**. Then the values are sent wirelessly to the LoRa gateway.

You can use community The Things Network to receive the data.

## What You Will Need

* [Core Module](https://shop.bigclown.com/core-module)
* [LoRa Module](https://shop.bigclown.com/lora-module)
* [Mini Battery Module](https://shop.bigclown.com/mini-battery-module)
* [Climate Module](https://shop.bigclown.com/climate-module)

## Firmware Upload

### Step 1: Download the latest [**BigClown Playground**](https://github.com/bigclownlabs/bch-playground/releases/latest)

### Step 2: Connect the Core Module to your computer.

### Step 3: In Playground, go to the **Firmware** tab, select `bcf-lora-climate-monitor` and flash the firmware.

### Step 4: After upload, the red LED on the Core Module will turn on for 2 seconds, then it will turn off.

## LoRa Configuration

For configuring the LoRa keys please follow [LoRa AT Commands Configuration](../tutorials/lora-at-commands-configuration.md) tutorial.

## Transmitting the data

The LoRa Climate Monitor sends a LoRa packet when:

* After power-up, when the batteries are inserted
* Every 15 minutes when the measure values are the same
* After pressing the button
* When you type `AT$SEND` to the console

## Reading the Data

The data are encoded in the LoRa message. You need to extract the right bits to get the values back. This is explained in the [README.md file](https://github.com/bigclownlabs/bcf-lora-climate-monitor/blob/master/README.md#buffer). You can also use the `decode.py`python [script in the repository](https://github.com/bigclownlabs/bcf-lora-climate-monitor). In the same directory there is also `decode.js` which you can use in the TTN backend to decode values and send them for example directly to Ubidots.

You can pass the received HEX string as a parameter for the `decode.py`:

```text
>>> python3 decode.py 011b0100f5600024c313

Header : UPDATE
Voltage : 2.7
Orientation : 1
Temperature : 24.5
Humidity : 48.0
Illuminance : 36
Pressure : 99878
```

