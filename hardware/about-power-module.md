# About Power Module

![](../.gitbook/assets/_basics_module-overview_power-module.png)

The **Power Module** allows you to connect a 5 V DC power adapter via a standard 2.1 mm power jack socket. It features a **high-current relay** \(230 V AC / 16 A\) to control your appliances. Also you can drive a **digital LED strip** with it \(compatible with WS2812B\).

| \*\*\*\*[**E-shop**](https://shop.bigclown.com/power-module)\*\*\*\* | [**Schematic Drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-power) | [**SDK Library**](https://sdk.bigclown.com/group__bc__module__power) | [**Header File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/inc/bc_module_power.h) | [**Source File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/src/bc_module_power.c) |
| :---: | :---: | :---: | :---: | :---: |


This module can power a BigClown node thanks to its integrated LDO regulator. The LDO generates 3.3 V output from the 5 V input.

Reliability is important - that's why we have implemented a **smart**overvoltage, undervoltage and reverse polarity **protection** on the power jack input. This feature guarantees the input voltage range to always stay within the proper limits.

There are also two 5-pin sockets available. These make it possible to connect BigClown tags.

### Features <a id="features"></a>

* 5 V DC power adapter input \(2.1 mm jack\) \(1\)
* Input voltage range: 4.2 V to 5.8 V
* High-current relay output \(230 V AC / 16 A\)
* Integrated LDO with 3.3 V output voltage
* Addressable/digital RGB\(W\) LED strip output \(1\)
* Integrated voltage translator \(3.3 V to 5 V\)
* 2x position for a BigClown tag
* Overvoltage, undervoltage and reverse polarity protection
* Pluggable 3-pin terminal block for relay output
* Pluggable 3-pin terminal block for digital LED strip
* Operating temperature range: -20 to 70 °C
* Mechanical dimensions: 88 x 55 mm

Note \(1\): Maximum allowed current is 6 A.

### Resources <a id="resources"></a>

* [**Documentation**](https://www.bigclown.com/doc/hardware/about-power-module/)
* [**Schematic drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-power)

### Firmware Projects <a id="firmware-projects"></a>

* [**Generic firmware**](https://github.com/bigclownlabs/bcf-generic-node/releases)

  Note: Use firmware for node-power-module and type and length of LED strip \(optional\)

* [**Radio Power Controller and LED strip**](https://github.com/bigclownlabs/bcf-radio-power-controller/releases) [**\(documentation\)**](https://www.bigclown.com/doc/projects/radio-smart-led-strip/)

