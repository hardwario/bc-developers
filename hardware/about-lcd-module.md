# About LCD Module

![](../.gitbook/assets/_basics_module-overview_lcd-module.png)

The **LCD Module** uses a unique technology - the so-called **memory display** developed by Sharp. It provides a resolution of 128 x 128 pixels in 1.28 inch size. It implements an **ultra-low-power display controller**, so you can have active graphical display with a long service time from batteries.

| \*\*\*\*[**E-shop**](https://shop.bigclown.com/lcd-module-bg)\*\*\*\* | [**Schematic Drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-lcd) | [**SDK Library**](https://sdk.bigclown.com/group__bc__module__lcd) | [**Header File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/inc/bc_module_lcd.h) | [**Source File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/src/bc_module_lcd.c) |
| :---: | :---: | :---: | :---: | :---: |


You can control your application using the **two buttons** located below the LCD screen. The module is also equipped with a **gesture sensor** \(Avago APDS-9960\). This circuit, composed of the infrared transmitter and four directional photodiodes responding to different wavelengths, can also be used to measure the light intensity and color or as a proximity sensor.

The **LCD Module** also includes six RGB LEDs that can be used to indicate status or as a light alarm.

A typical use-case for the **LCD Module** is a wireless thermostat, or it can directly display values from various sensors located both indoors and outdoors.

The **LCD Module** can also function as a unique status display for the Turris Omnia router.

### Features <a id="features"></a>

* Memory LCD LS013B7DH03 \(Sharp\)
* Display resolution: 128 x 128 pixels
* Display size: 1.28 inch
* Two user buttons
* Gesture sensor APDS-9960 \(Avago\)
  * Movement
  * Light intensity
  * Proximity
* 6x miniature RGB LED
* Typical consumption &lt; 16 μA
* Operating voltage range: 2.7 V to 3.3 V
* Operating temperature range: -20 to 70 °C
* Dimensions: 33 x 55 mm

### Resources <a id="resources"></a>

* [**Documentation**](https://www.bigclown.com/doc/hardware/about-lcd-module/)
* [**Schematic drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-lcd)

### Firmware Projects <a id="firmware-projects"></a>

* [**Generic firmware**](https://github.com/bigclownlabs/bcf-generic-node/releases)
* [**Radio LCD Thermostat**](https://github.com/bigclownlabs/bcf-radio-lcd-thermostat/releases)

