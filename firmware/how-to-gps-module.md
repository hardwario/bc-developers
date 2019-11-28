# How to: GPS Module

GPS Module can be used for getting position, time, date and altitude.

## How It Works

Thanks to the [SDK](https://sdk.bigclown.com/group__bc__module__gps.html), setting up and using the GPS Module is very simple. You have to do only two things:

1. Initialize the GPS Module
2. Program the event handler \(what should happen when GPS Module gets update\)

```c
#include <application.h>

bc_led_t led;
bc_led_t gps_led_r;
bc_led_t gps_led_g;

void gps_module_event_handler(bc_module_gps_event_t event, void *event_param)
{
    if (event == BC_MODULE_GPS_EVENT_START)
    {
        bc_log_info("APP: Event BC_MODULE_GPS_EVENT_START");

        bc_led_set_mode(&gps_led_g, BC_LED_MODE_ON);
    }

    else if (event == BC_MODULE_GPS_EVENT_STOP)
    {
        bc_log_info("APP: Event BC_MODULE_GPS_EVENT_STOP");

        bc_led_set_mode(&gps_led_g, BC_LED_MODE_OFF);
    }

    else if (event == BC_MODULE_GPS_EVENT_UPDATE)
    {
        bc_led_pulse(&gps_led_r, 50);

        bc_module_gps_time_t time;

        if (bc_module_gps_get_time(&time))
        {
            bc_log_info("APP: Date: %04d-%02d-%02d",
                        time.year, time.month, time.day);

            bc_log_info("APP: Time: %02d:%02d:%02d",
                        time.hours, time.minutes, time.seconds);
        }

        bc_module_gps_position_t position;

        if (bc_module_gps_get_position(&position))
        {
            bc_log_info("APP: Lat: %03.5f", position.latitude);
            bc_log_info("APP: Lon: %03.5f", position.longitude);
        }

        bc_module_gps_altitude_t altitude;

        if (bc_module_gps_get_altitude(&altitude))
        {
            bc_log_info("APP: Altitude: %.1f %c", altitude.altitude, tolower(altitude.units));
        }

        bc_module_gps_quality_t quality;

        if (bc_module_gps_get_quality(&quality))
        {
            bc_log_info("APP: Fix quality: %d", quality.fix_quality);
            bc_log_info("APP: Satellites: %d", quality.satellites_tracked);
        }

        bc_module_gps_invalidate();
    }

    else if (event == BC_MODULE_GPS_EVENT_ERROR)
    {
        bc_log_info("APP: Event BC_MODULE_GPS_EVENT_ERROR");
    }
}

void application_init(void)
{
    bc_log_init(BC_LOG_LEVEL_DUMP, BC_LOG_TIMESTAMP_ABS);

    bc_led_init(&led, BC_GPIO_LED, false, false);
    bc_led_set_mode(&led, BC_LED_MODE_ON);

    if (!bc_module_gps_init())
    {
        bc_log_error("APP: GPS Module initialization failed");
    }

    else
    {
        bc_module_gps_set_event_handler(gps_module_event_handler, NULL);
        bc_module_gps_start();
    }

    bc_led_init_virtual(&gps_led_r, BC_MODULE_GPS_LED_RED, bc_module_gps_get_led_driver(), 0);
    bc_led_init_virtual(&gps_led_g, BC_MODULE_GPS_LED_GREEN, bc_module_gps_get_led_driver(), 0);
}

```

This code will send via `bc_log` date, time, position, number of satellites module sees and fix quality. You can [compile](toolchain-setup.md) it and see logs via `bcf --log`.

