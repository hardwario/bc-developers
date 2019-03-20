# About Mini Battery Module

![](../.gitbook/assets/_basics_module-overview_mini-battery-module.png)

The **Mini Battery Module** is designed as a power supply source for the battery-operated units. The integrated low-power boost converter provides an excellent efficiency from the **two AAA 1.5 V Alkaline** cells. It features a bottom-entry sockets, so the overall profile of the unit you build remains low.

| \*\*\*\*[**E-shop**](https://shop.bigclown.com/mini-battery-module)\*\*\*\* | [**Schematic Drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-battery-mini) | [**SDK Library**](https://sdk.bigclown.com/group__bc__module__battery) | [**Header File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/inc/bc_module_battery.h) | [**Source File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/src/bc_module_battery.c) |
| :---: | :---: | :---: | :---: | :---: |


The load disconnect circuit can disconnect the batteries if any other power supply source is connected to the system \(e.g. AC adapter or USB cable\). The **battery voltage can be measured** on one of the analog inputs of the standardized header \(P0/A0/TXD0\).

### Features <a id="features"></a>

* Highly efficient DC/DC converter TPS61099 \(TI\)
* Very low quiescent current &lt;5 μA
* Efficiency up to 93% at 10 mA
* Recommended types of batteries:
  * 2x AAA 1.5 V Alkaline, or
  * 2x AAA Eneloop NiMH
* Rated output voltage 3.1 V
* Circuit for disconnecting the battery
* Reverse polarity protection
* Input voltage measurement via ADC input
* Operating temperature range: -20 to 70 °C
* Dimensions: 33 x 55 mm

### Resources <a id="resources"></a>

* [**Documentation**](about-mini-battery-module.md)
* [**Schematic drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-battery-mini)

### Firmware Projects <a id="firmware-projects"></a>

* [**Generic firmware**](https://github.com/bigclownlabs/bcf-generic-node/releases)

  Note: Use firmware for node-battery-mini

