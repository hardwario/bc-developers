# About CO2 Module

![](../.gitbook/assets/_basics_module-overview_co2-module.png)

The **CO2 Module** is a gas sensor for measuring the **carbon dioxide \(CO₂\) concentration**. This module achieves ±50 ppm accuracy. It uses a non-dispersive infrared \(NDIR\) sensor manufactured in Sweden. Thanks to its **low-power operation** it can be powered from batteries for years.

| \*\*\*\*[**E-shop**](https://shop.bigclown.com/co2-module)\*\*\*\* | [**Schematic Drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-co2) | [**SDK Library**](https://sdk.bigclown.com/group__bc__module__co2) | [**Header File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/inc/bc_module_co2.h) | [**Source File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/src/bc_module_co2.c) |
| :---: | :---: | :---: | :---: | :---: |


Carbon dioxide \(or CO₂\) is a colorless and odorless gas that is vital to life on Earth. Its nominal concentration is about 400 ppm \(0.04 %\). There are many occurrences of CO₂ in nature. For example humans produce CO₂ when exhaling.

**The high concentration of CO₂ leads to acidity and various health related problems.**

We have equipped the LP8 sensor with additional circuitry for efficient power management and I²C-only interfacing. This module also features three 5-pin sockets allowing you to connect BigClown tags.

### Features <a id="features"></a>

* Carbon dioxide \(CO₂\) sensor LP8 \(SenseAir\)
* Non-dispersive infrared \(NDIR\) technology
* Measurement range of CO₂: 0 to 10 000 ppm
* Measurement accuracy: ±50 ppm CO₂ ±3 % of reading \(Note 1\)
* I²C-only interface \(integrated UART bridge and I/O expander\)
* Constant current source for 470 mF supercap
* Long battery life time
* 3 sockets for a BigClown tag
* Low power consumption:
  * 6 µA \(6 measurements per hour\)
  * 61 µA \(1 measurement per minute\)
* Operating voltage range: 3 V to 3.6 V
* Operating temperature range: 0 to 50 °C
* Mechanical dimensions: 88 x 55 mm

Note 1: Accuracy ±50 ppm is achieved after 24 days of operation and auto calibration process.

### Resources <a id="resources"></a>

* [**Documentation**](about-co2-module.md)
* [**Schematic drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-co2)

### Firmware Projects <a id="firmware-projects"></a>

* [**Generic firmware**](https://github.com/bigclownlabs/bcf-generic-node/releases)
* [**Radio CO2 Monitor**](https://github.com/bigclownlabs/bcf-radio-co2-monitor/releases) [**\(documentation\)**](https://www.bigclown.com/doc/projects/radio-co2-monitor/)

