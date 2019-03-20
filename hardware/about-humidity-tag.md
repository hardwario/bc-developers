# About Humidity Tag

![](../.gitbook/assets/_basics_module-overview_humidity-tag.png)

The **Humidity Tag** uses a high-accuracy **humidity sensor** SHT20 with a typical accuracy of ±3 % from 20 % to 80 %. This sensor is digital and calibrated. It communicates using an I²C bus and features a very low power operation and shutdown mode.

| \*\*\*\*[**E-shop**](https://shop.bigclown.com/humidity-tag)\*\*\*\* | [**Schematic Drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-tag-humidity) | [**SDK Library**](https://sdk.bigclown.com/group__bc__tag__humidity) | [**Header File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/inc/bc_tag_humidity.h) | [**Source File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/src/bc_tag_humidity.c) |
| :---: | :---: | :---: | :---: | :---: |


Relative humidity is the essential attribute of the environment we live in. The recommended indoor range is between 30 % and 60 %.

**Values below this range \(dry air\) can lead to various health issues. On the other hand, the values above this range may result in troubles with moisture.**

### Features <a id="features"></a>

* Integrated humidity sensor SHT20 \(Sensirion\)
* Communication using I²C bus
* Measurement range: 0 % to 100 %
* Measurement accuracy: ±2 %
* Optional interrupt output
* Operating current: 10 µA
* Operating voltage range: 1.8 V to 3.3 V
* Operating temperature range: -40 to 125 °C
* Mechanical dimensions: 16 x 16 mm

### Resources <a id="resources"></a>

* [**Documentation**](about-humidity-tag.md)
* [**Schematic drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-tag-humidity)

### Firmware Projects <a id="firmware-projects"></a>

* [**Generic firmware**](https://github.com/bigclownlabs/bcf-generic-node/releases)
* [**Radio CO2 Monitor**](https://github.com/bigclownlabs/bcf-radio-co2-monitor/releases) [**\(documentation\)**](https://www.bigclown.com/doc/projects/radio-co2-monitor/)

