# How to: RTC clock

Real Time Clock \(RTC\) is a hardware peripheral in STM32 microcontroller. It is used in scheduler for task planning and also can measure real time. You can save date and time into its hardware registers and the clock is running even if you reflash or reset the processor.

Because the STM32 in LQFP48 package does not have battery backup pin, you have to keep connected at least single source of power if you would like to keep the RTC counting. So if you need to change the batterry module you can keep the Core Module connected over USB to keep the RTC running.

Core Module has 32 768 Hz crystal which is connected to the RTC peripheral.

> All the RTC APIs are in our [Doxygen generated SDK page](http://sdk.bigclown.com/group__bc__rtc.html)

## RTC Structure

RTC structure contains year, month, date, day of the week. For time there are hours, minutes, seconds. If you read the RTC then the `timestamp` is fileld with proper UNIX timestamp.

```text
//! @brief RTC date and time structure
typedef struct
{
    uint8_t seconds;     //!< Seconds parameter, from 00 to 59
	uint16_t subseconds; //!< Subsecond downcounter. When it reaches zero, it's reload value is the same as @ref RTC_SYNC_PREDIV
	uint8_t minutes;     //!< Minutes parameter, from 00 to 59
	uint8_t hours;       //!< Hours parameter, 24Hour mode, 00 to 23
	uint8_t day;         //!< Day in a week, from 1 to 7
	uint8_t date;        //!< Date in a month, 1 to 31
	uint8_t month;       //!< Month in a year, 1 to 12
	uint8_t year;        //!< Year parameter, 00 to 99, 00 is 2000 and 99 is 2099
	uint32_t timestamp;  //!< Seconds from 01.01.1970 00:00:00
} bc_rtc_t;
```

## Initialization

Initialization of RTC is automatic. The RTC is initialized everytime the YEAR register is set to zero. So if you use just the time registers you should set at least value 1 to the year register. This way the RTC is not reinitialized after reset which has a side-effect of stopping RTC counter for a second.

## Year register

Year register can hold values **00** to **99**. So before writing current year to this register you have to subtract 2000 and when you print the date you have to add 2000.

## Set date and time

```c
bc_rtc_t rtc;

rtc.hours = 11;
rtc.minutes = 26;
rtc.seconds = 00;

rtc.year = 19; // You have to subtract 2000
rtc.month = 5;
rtd.date = 16;

bc_rtc_set_date_time(&rtc);
```

## Read date and time

```c
bc_rtc_t datetime;
bc_rtc_get_date_time(&datetime);
bc_log_debug("$DATE: \"%d-%02d-%02dT%02d:%02d:%02dZ\"", 2000 + datetime.year, datetime.month, datetime.date, datetime.hours, datetime.minutes, datetime.seconds);
```

## Example projects

{% embed url="https://github.com/bigclownprojects/bcf-lcd-clock-with-stopwatch" %}



