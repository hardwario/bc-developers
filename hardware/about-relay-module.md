# About Relay Module

![](../.gitbook/assets/_basics_module-overview_relay-module.png)

The **Relay Module** is suitable for switching small power appliances - e.g. LED strip, cooling fan, siren, buzzer, garage door opener, etc. It features a **bistable \(or latching\) relay** and that makes it suitable for battery-operated applications - the relay simply remembers its state.

| \*\*\*\*[**E-shop**](https://shop.bigclown.com/relay-module)\*\*\*\* | [**Schematic Drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-relay) | [**SDK Library**](https://sdk.bigclown.com/group__bc__module__relay) | [**Header File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/inc/bc_module_relay.h) | [**Source File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/src/bc_module_relay.c) |
| :---: | :---: | :---: | :---: | :---: |


The energy is needed only during transition state. Once the new state has been set, it is not necessary to energize the relay's coil anymore. Switching period is indicated using the green LED \(in software referred as "true state"\), or red LED \(in software referred as "false state"\).

### Features <a id="features"></a>

* Bistable \(latching\) relay for switching loads up to 60 W:
  * 12 V DC / 5 A
  * 24 V DC / 2.5 A
* Control using I²C bus
* Suitable for battery-operated applications
* Energy for coil is needed only during the transition states
* Red and green LEDs indicate the coil energizing
* Operating voltage range: 3.0 to 3.6 V
* Operating temperature range: -20 to 70 °C
* Mechanical dimensions: 33 x 55 mm

### Resources <a id="resources"></a>

* [**Documentation**](about-relay-module.md)
* [**Schematic drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-relay)

### Firmware Projects <a id="firmware-projects"></a>

* [**Generic firmware**](https://github.com/bigclownlabs/bcf-generic-node/releases)

