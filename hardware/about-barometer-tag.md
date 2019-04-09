# About Barometer Tag

![](../.gitbook/assets/_basics_module-overview_barometer-tag.png)

The **Barometer Tag** allows you to measure absolute pressure in the range from 20 kPa to 110 kPa, or altitude above the sea level in meters. It uses a low-power I²C sensor MPL3115A2 with an absolute accuracy of ±0.4 kPa. It features a very low active and standby current.

| \*\*\*\*[**E-shop**](https://shop.bigclown.com/barometer-tag)\*\*\*\* | [**Schematic Drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-tag-barometer) | [**SDK Library**](https://sdk.bigclown.com/group__bc__tag__barometer) | [**Header File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/inc/bc_tag_barometer.h) | [**Source File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/src/bc_tag_barometer.c) |
| :---: | :---: | :---: | :---: | :---: |


Monitoring of absolute pressure is useful for weather forecast and it is also an important parameter in biometeorology because the absolute pressure can affect our health.

### Features <a id="features"></a>

* Absolute pressure sensor MPL3115A2 \(NXP\)
* Sensor only needs I²C bus
* Pressure range: from 20 kPa to 110 kPa
* Altitude range: from -698 to 11,775 m
* Absolute accuracy: ±0.4 kPa
* Optional interrupt output
* Power consumption:
  * 40 µA average current \(1 Hz sample rate\)
  * 2 µA standby current
* Operating voltage range: 2.0 V to 3.6 V
* Operating temperature range: -40 to 85 °C
* Mechanical dimensions: 16 x 16 mm

### Resources <a id="resources"></a>

* [**Documentation**](about-barometer-tag.md)
* [**Schematic drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-tag-barometer)

### Firmware Projects <a id="firmware-projects"></a>

* [**Generic firmware**](https://github.com/bigclownlabs/bcf-generic-node/releases)
* [**Radio CO2 Monitor**](https://github.com/bigclownlabs/bcf-radio-co2-monitor/releases) [**\(documentation\)**](../projects/radio-co2-monitor.md)

