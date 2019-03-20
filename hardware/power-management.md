# Power Management

{% hint style="danger" %}
This document goes deep into technical details and explains the BigClown power management on the hardware level.
{% endhint %}

The **BigClown IoT Kit** has been designed the way to allow connection of multiple power sources.

For example, this allows the **Core Module** to be powered from a USB cable and also have batteries inserted in the **Battery Module** at the same time. BigClown automatically solves the problem selecting the appropriate power sources.

What does it mean? For example, when an external power supply \(adapter or USB\) is connected, the battery is disconnected and discharged. It is also possible to have multiple external sources connected at the same time - for example, the adapter plugged into the **Power Module** and the USB cable in the **Core Module**.

{% hint style="info" %}
In this case, the module that is located in the physically lower layer will take priority and will be the one that will deliver power to the system.
{% endhint %}

## How It Works

The BigClown header has two signals for system power distribution:

1. **VDD** - Positive supply rail either 3.1 V when powering from batteries or 3.3 V from the external power supply
2. **GND** - Ground \(negative rail\)

The module that is able to deliver power in the system is called the **energizer**. The energy is supplied either using an external power supply, or using batteries. In both cases, an **energizer** contains the electronics circuit for intelligent power management.

This additional electronics circuit controls \(or is controlled by\) two auxiliary signals on the BigClown header:

### Signal **BAT\_OFF**

This signal disconnects the batteries and prevents their discharging when other power source is available and the batteries are not needed.

{% hint style="info" %}
An OR-ing diode is used so multiple modules driving this signal at the same time do not interfere.
{% endhint %}

### **Signal VDD\_OFF**

This signal is physically split into two parts:

* Signal **VDD\_OFF\_IN**

  This signal is on the bottom side of the module \(the side with the pins\) and it disconnects the power supply output of the given module.

* Signal **VDD\_OFF\_OUT**

  This signal is on the top side of the module \(the side with the sockets\) and it is chained to the **VDD\_OFF\_IN** signal of the module above the given one.

{% hint style="info" %}
The split is easy to implements thanks to SMT technology of the connectors. Pins and sockets on the header are not electrically connected unless a via is used explicitly.
{% endhint %}

## Implementation

This is the example of the eletronics circuit of the battery **energizer**:

![](../.gitbook/assets/_hardware_power-management_energizer-circuit-battery.png)

This is the example of the eletronics circuit of the **energizer** powered from an external power supply:

![](../.gitbook/assets/_hardware_power-management_energizer-circuit-external.png)

Whether it is a battery power or a external power source, the two P-channel MOSFETs are always on the output of the power supply in the so-called back-to-back configuration. This guarantees complete power supply disconnect and no backflow current is possible when the power supply is not operating.

## Related Documents

* [**Header and Signals**](header-pinout.md)

