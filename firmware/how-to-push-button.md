# How to: Push Button

You can control your device in many ways - you can add switches, sensors, Wi-Fi connection, etc. But the most simple way is to use button\(s\) integrated in Core module.

## Requirements

* Core module
* USB cable
* [Example code](https://github.com/bigclownlabs/bcf-sdk/tree/master/_examples/button)

## Integrated Buttons

Core module comes with two buttons - Reset and Boot. You can take a look at [schematics](https://github.com/bigclownlabs/bc-hardware/tree/master/out/bc-module-core). _Reset \(R\)_ button is used for resetting the Core module - which is de facto equal to unplugging and replugging the power/USB cable. _Boot \(B\)_ button can be used as you wish.

This tutorial shows how to work with integrated button, but it can be used for your own buttons or switches.

{% hint style="info" %}
**As always...**  
... all available SDK functions for buttons can be found [here](https://sdk.bigclown.com/group__bc__button.html).
{% endhint %}

## Recognizable Button Events

_BC\_BUTTON\_EVENT\_PRESS_ and _BC\_BUTTON\_EVENT\_RELEASE_ are pretty straightforward - the first one stands for pressing the button and the second one for releasing the button.

_BC\_BUTTON\_EVENT\_CLICK_ event is recognized, when button is **pressed and held** for period of time **shorter than defined** \(can be defined by [_bc\_button\_set\_click\_timeout_](https://sdk.bigclown.com/group__bc__button.html#ga88fd3c911e2feb4f5ea8e1eb511ad8e5)\)

_BC\_BUTTON\_EVENT\_HOLD_ event is recognized, when button is **pressed and held** for period of time **longer than defined** \(can be defined by [_bc\_button\_set\_hold\_timeout_](https://sdk.bigclown.com/group__bc__button.html#ga3ec362aaaa409c85170310074cc5a320)\)

## Example

First, an instance of button is needed. You can achieve this by adding this line:`bc_button_t button;`

Button is initiated by function

* `*self` is an address to the instantiated button
* `gpio_channel` is GPIO channel number - defined as _enum_, more in [SDK](https://sdk.bigclown.com/group__bc__gpio.html)
* `gpio_pull` stands for GPIO pull up/down settings
* `idle_state` - state of a GPIO pin, when button **is not** pressed

In our example, we call init function this way:

```c
bc_button_init(&button, BC_GPIO_BUTTON, BC_GPIO_PULL_DOWN, 0);
```

Then we need to define _event handler_ - what function to call when something happens with the button.

```c
bc_button_set_event_handler(&button, button_event_handler, NULL);
```

In other words: _when button is triggered, call function called 'button\_event\_handler' with no additional parameters_

In the _button\_event\_handler_ function we mainly compare the _event_ parameter with callback events defined in [bc\_button\_event\_t](https://sdk.bigclown.com/group__bc__button.html#ga6584b74ad24dd2ca8048fd72c73426fa).

In this example we will use _\_HOLD_ and _\_PRESS_ events for better understanding. Programmed Core module will work by these rules:

* when button is **held for 1.5 seconds** \(or more\), LED starts to blink fast
* when button is **pressed** \(simple short press\), LED goes off

To set the 1.5 second interval we can use _bc\_button\_set\_hold\_time_ function \(inside _application\_init\(\)_\) `bc_button_set_hold_time(&button, 1500);`

Everything else is defined in the _button\_event\_handler_ function.

```c
void button_event_handler(bc_button_t *self, bc_button_event_t event, void *event_param)
{ 
 (void) self; (void) event_param;
  if (event == BC_BUTTON_EVENT_PRESS)
  {
   bc_led_set_mode(&led, BC_LED_MODE_OFF);
   } 
   
  else if (event == BC_BUTTON_EVENT_HOLD )
  {
    bc_led_set_mode(&led,  BC_LED_MODE_BLINK_FAST);
  }
}
```

Full _ready-to-flash_ code for this example can be found at [Github](https://github.com/bigclownlabs/bcf-sdk/tree/master/_examples/button).

