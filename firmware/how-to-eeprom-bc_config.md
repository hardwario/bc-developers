# How to: EEPROM bc\_config

`bc_config` functions helps you to easily create a variable or structure of variables that are saved in internal EEPROM memory.

Library will automatically initialize your configuration when:

* it runs first time
* if the signature parameter is different
* if the new configuration structure has different length
* if the EEPROM is corrupted

> Doxygen documentation of [bc\_config](http://sdk.bigclown.com/group__bc__config.html)

## Initialization

The first parameter, `signature` , is unique number for your firmware. This way if you load a different firmware to the Core Module that is using configuration structure with the same length, the library will see that and initialize the confguration properly again.

The last parameter \*init\_config can be:

* `NULL` - the config structure is zeroed when initialized
* pointer to structure - the `init_config` is copied to the `config` structure when initialized

```text
// Load configuration
bc_config_init(0x12345678, &config, sizeof(config), NULL);
```

## Code Example

```text
// Example structure that save configuration of PIR detector
typedef struct config_t
{
    uint16_t report_interval;
    uint8_t pir_sensitivity;
    uint16_t pir_deadtime;
    
} config_t;

config_t config;

void application_init()
{
    // Load configuration
    bc_config_init(0x12345678, &config, sizeof(config), NULL);
    
    // Change parameter
    config.report_interval = 500;
    
    // Save config to EEPROM
    bc_config_save();
    
    // Reset configuration
    bc_config_reset();
}
```

