# About Battery Module

![](../.gitbook/assets/_basics_module-overview_battery-module.png)

The **Battery Module** is designed as a power supply source for the battery-operated units. The integrated low-power buck converter provides an excellent efficiency from the **four AAA 1.5 V Alkaline** cells. It also features an extra 5-pin socket where you can connect a BigClown tag.

| [**E-shop**](https://shop.bigclown.com/battery-module) | [**Schematic Drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-battery) | [**SDK Library**](https://sdk.bigclown.com/group__bc__module__battery) | [**Header File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/inc/bc_module_battery.h) | [**Source File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/src/bc_module_battery.c) |
| :---: | :---: | :---: | :---: | :---: |


The load disconnect circuit can disconnect the batteries if any other power supply source is connected to the system \(e.g. AC adapter or USB cable\). The **battery voltage can be measured** on one of the analog inputs of the standardized header \(P0/A0/TXD0\).

If the for AAA batteries are not suitable for your application, you can use the **external voltage input**, which can handle up to 10 V. You can find the external input on the two pins in the middle. These pins are compatible with the popular JST connector used for Lithium batteries.

Another useful feature is a **prototyping area** for soldering your own circuits.

### Features <a id="features"></a>

* High-efficiency buck converter TPS62745 \(TI\)
* Ultra-low quiescent current: 400 nA
* Recommended battery types:
  * 4x AAA 1.5 V Alkaline or
  * 4x AAA Eneloop NiMH
* Output supply voltage: 3.1 V
* Battery disconnect circuit
* Battery voltage measurement using an ADC input
* Prototyping area for soldering custom circuits
* One extra position for BigClown tag
* Operating voltage range: 3.3 to 10 V
* Operating temperature range: -20 to 70 °C
* Mechanical dimensions: 88 x 55 mm

### Resources <a id="resources"></a>

* [**Documentation**](about-battery-module.md)
* [**Schematic drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-battery)

### Firmware Projects <a id="firmware-projects"></a>

* [**Generic firmware**](https://github.com/bigclownlabs/bcf-generic-node/releases)

  Note: Use firmware for node-battery-standard

