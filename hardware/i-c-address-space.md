# I²C Address Space

The following table lists the I²C addresses used across the BigClown system.

All addresses are provided in a 7-bit format.

| Address | Chip | BigClown product | Remark |
| :--- | :--- | :--- | :--- |
| 0x08 | NT3H2011 | [NFC Tag](https://shop.bigclown.com/nfc-tag) | Changed from default to avoid collision |
| 0x19 | LIS2DH12 | [Core Module](https://shop.bigclown.com/core-module) | Channel I2C0 |
| 0x20 | TCA9534 | IQRF Module |  |
| 0x21 | TCA9534 | GPS Module |  |
| 0x22 | TCA9534 | RFID Module |  |
| 0x23 | TCA9534 | Infragrid Module |  |
| 0x24 | TCA9534 | Ethernet Module |  |
| 0x25 | TCA9534 |  | Reserved |
| 0x26 | TCA9534 |  | Reserved |
| 0x27 | TCA9534 |  | Reserved |
| 0x38 | TCA9534A | [CO2 Module](https://shop.bigclown.com/co2-module) |  |
| 0x39 | TCA9534A |  | Reserved |
| 0x3a | TCA9534A |  | Reserved |
| 0x3b | TCA9534A | [Relay Module](https://shop.bigclown.com/relay-module) | Default address |
| 0x3c | TCA9534A | [LCD Module](https://shop.bigclown.com/lcd-module-bg) |  |
| 0x3d | TCA9534A |  | Reserved |
| 0x3e | TCA9534A | [Sensor Module](https://shop.bigclown.com/sensor-module) | Default address |
| 0x3f | TCA9534A | [Relay Module](https://shop.bigclown.com/relay-module) | Alternate address |
| 0x40 | SHT20 | [Humidity Tag](https://shop.bigclown.com/humidity-tag) \(R3.x+\), [Climate Module](https://shop.bigclown.com/climate-module) |  |
| 0x40 | HDC2080 | [Humidity Tag](https://shop.bigclown.com/humidity-tag) \(R2.x+\) | Default address |
| 0x41 | HDC2080 | [Humidity Tag](https://shop.bigclown.com/humidity-tag) \(R2.x+\) | Alternate address |
| 0x44 | OPT3001 | [Lux Meter Tag](https://shop.bigclown.com/lux-meter-tag), [Climate Module](https://shop.bigclown.com/climate-module) | Default address |
| 0x45 | OPT3001 | [Lux Meter Tag](https://shop.bigclown.com/lux-meter-tag) | Alternate address |
| 0x48 | TMP112 | [Temperature Tag](https://shop.bigclown.com/temperature-tag), [Climate Module](https://shop.bigclown.com/climate-module) | Default address |
| 0x49 | TMP112 | [Temperature Tag](https://shop.bigclown.com/temperature-tag) | Alternate address |
| 0x49 | TMP112 | [Core Module](https://shop.bigclown.com/core-module), [Cloony](https://shop.bigclown.com/cloony/) | Channel I2C0 |
| 0x4d | SC16IS740 | [CO2 Module](https://shop.bigclown.com/co2-module) I2C to UART bridge | Channel I2C0 |
| 0x4e | SC16IS750 | RS-485 Module I2C to UART bridge | Channel I2C0 |
| 0x4f | SC16IS750 | RS-232 Module I2C to UART bridge | Channel I2C0 |
| 0x58 | SGP30 | [VOC Tag](https://shop.bigclown.com/voc-tag) | Default address |
| 0x5f | HTS221 | [Humidity Tag](https://shop.bigclown.com/humidity-tag) \(R1.x\) |  |
| 0x60 | MPL3115A2 | [Barometer Tag](https://shop.bigclown.com/barometer-tag), [Climate Module](https://shop.bigclown.com/climate-module) |  |
| 0x64 | ATSHA204A | [Core Module](https://shop.bigclown.com/core-module), [Radio Dongle](https://shop.bigclown.com/radio-dongle), [Cloony](https://shop.bigclown.com/cloony/) | Channel I2C0 |
| 0x64 | ATSHA204A | [Radio Dongle](https://shop.bigclown.com/radio-dongle) | Channel I2C1 |

{% hint style="info" %}
Addresses 0x00-0x07 and 0x78-0x7F are I2C reserved addresses and cannot be used.
{% endhint %}

## References

* [**Adafruid I2C address compilation**](https://learn.adafruit.com/i2c-addresses/the-list)

