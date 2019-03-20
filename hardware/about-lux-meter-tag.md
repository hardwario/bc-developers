# About Lux Meter Tag

![](../.gitbook/assets/_basics_module-overview_lux-meter-tag.png)

The **Lux Meter Tag** uses a high dynamic range **light intensity sensor** OPT3001 that can measure illuminance from 0.01 to 83,000 lux. This sensor is digital and calibrated. It communicates using an I²C bus and features a very low power operation and shutdown mode.

| \*\*\*\*[**E-shop**](https://shop.bigclown.com/lux-meter-tag)\*\*\*\* | [**Schematic Drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-tag-lux-meter) | [**SDK Library**](https://sdk.bigclown.com/group__bc__tag__lux__meter) | [**Header File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/inc/bc_tag_lux_meter.h) | [**Source File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/src/bc_tag_lux_meter.c) |
| :---: | :---: | :---: | :---: | :---: |


You can use the sensor to detect day and night or it could be used as auxiliary information about someone's presence.

The spectral response of the sensor tightly matches the photopic response of the human eye and includes **significant infrared rejection**.

### Features <a id="features"></a>

* Digital ambient light sensor OPT3001 \(TI\)
* Communication using I²C bus
* Measures in the range from 0.01 to 83,000 lux
* 23-bit effective dynamic range
* Optional interrupt output
* Power consumption:
  * Active current: 1.8 µA
  * Shutdown current: 0.3 µA
* Operating voltage range: 1.6 V to 3.6 V
* Operating temperature range: -20 to 70 °C
* Mechanical dimensions: 16 x 16 mm

### Resources <a id="resources"></a>

* [**Documentation**](about-lux-meter-tag.md)
* [**Schematic drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-tag-lux-meter)

### Firmware Projects <a id="firmware-projects"></a>

* [**Generic firmware**](https://github.com/bigclownlabs/bcf-generic-node/releases)

