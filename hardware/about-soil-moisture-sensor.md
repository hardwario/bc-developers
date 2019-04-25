# About Soil Moisture Sensor

![Pre-production Soil Moisture Sensor without coating](../.gitbook/assets/_hardware_about-soil-moisture-sensor_module.png)

The **Soil Moisture Sensor** is a modern, completely sealed capacitive moisture sensor with temperature sensor and calibration saved in its internal EEPROM. It is using 1-Wire communication protocol and has 3 wire cable that is 2 meters long. Many sensors can be connected to a single 1-Wire Master. The temperature sensor is located in the top part above the soil. The electronics is completely potted in a sealing compound to withstand all kind of weather.

The sensor returns soil moisture humidity values from 0 to 100%. Measuring is done by two copper strips inside the inner layers of the 4 layer PCB. This way the contacts are not exposed to direct humidity and do not oxidize.

The sensor comes already calibrated. Calibration is done in the water. It is also possible to use sensor to measure water level. 

Sensor is already supported in BigClown SDK with examples and projects. Arduino Library is in progress and will be ready in May 2019.

| [**E-shop**](https://shop.bigclown.com/soil-moisture-sensor/)\*\*\*\* | [**Schematic Drawing**](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-soil-sensor) | [**SDK Library**](https://sdk.bigclown.com/group__bc__soil__sensor.html) | [**Header File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/inc/bc_soil_sensor.h) | [**Source File**](https://github.com/bigclownlabs/bcf-sdk/blob/master/bcl/src/bc_soil_sensor.c) |
| :---: | :---: | :---: | :---: | :---: |


The sensor is using 1-Wire to I2C converter chip. Behind this converter all the chips are using I2C.

![Connection of the Soil Moisture Sensor to the Sensor Module](../.gitbook/assets/_hardware_abou-sensor-module_1-wire.png)

### Features <a id="features"></a>

* Soil moisture sensor 0-100%
* Fully digital design
* 1-Wire bus communication
* Possibility to connect multiple sensors in parallel
* Capacitance-to-digital converter ZSSC3123
* Digital temperature sensor TMP112
* Operating voltage range: 2.8 V to 5.5 V
* Operating temperature range: -40 to +85 °C
* Protection marking IP 68

### Firmware examples

* [How To: Soil Moisture Sensor](../firmware/how-to-soil-moisture-sensor.md)

### Projects <a id="firmware-projects"></a>

* [Radio Soil Sensor](../projects/radio-soil-sensor.md)

