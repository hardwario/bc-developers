# About Soil Moisture Sensor

![Pre-production Soil Moisture Sensor without coating](../.gitbook/assets/_hardware_about-soil-moisture-sensor_module.png)

The **Soil Moisture Sensor** is a modern, completely coated capacitive moisture sensor with temperature sensor and calibration saved in its internal EEPROM. It is using 1-Wire communication protocol and has 3 wire cable that is 2 meters long. Many sensors can be connected to a single 1-Wire Master.

The sensor returns soil moisture humidity values from 0 to 100%. The sensor comes already calibrated. Calibration is done in the water. It is also possible to use sensor to measure water level. The temperature sensor is placed in the top of the sensor near the cable.

Sensor is already supported in BigClown SDK. Arduino Library is in progress and will be ready in May 2019.

| [**E-shop**](https://shop.bigclown.com/soil-moisture-sensor/)\*\*\*\* | [**Schematic Drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-soil-sensor) | [**SDK Library**](https://sdk.bigclown.com/group__bc__soil__sensor.html) | [**Header File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/inc/bc_soil_sensor.h) | [**Source File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/src/bc_soil_sensor.c) |
| :---: | :---: | :---: | :---: | :---: |


The sensor is using 1-Wire to I2C converter chip. Behind this converter all the chips are using I2C.

![Connection of the Soil Moisture Sensor to the Sensor Module](../.gitbook/assets/_hardware_abou-sensor-module_1-wire.png)

### Features <a id="features"></a>

* Soil Moisture 0-100%
* Temperature sensor
* Calibrated - calibration data in internal EEPROM
* 1-Wire communication
* Many sensors on a single 1-Wire bus
* Supply voltage 3.0 - 5.5 V

### Firmware examples

* [How To: Soil Moisture Sensor](../firmware/how-to-soil-moisture-sensor.md)

### Projects <a id="firmware-projects"></a>

* [Radio Soil Sensor](../projects/radio-soil-sensor.md)

