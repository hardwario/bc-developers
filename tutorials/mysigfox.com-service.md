# MySigfox.com Service

MySigfox.com is our online service, which acts as a bridge between Sigfox Backend and your server. Customers who buy our [Sigfox module](https://shop.bigclown.com/bundle-sigfoxmodule-mysigfoxplatinum3y/) with 3-years connectivity can use this service to get data sent by their modules to Sigfox network. This service is free to use.

## Device Registration

When you order Sigfox module with connectivity, you will receive it together with device ID and Token. Device ID is unique alphanumeric string identifying your module. Token allows you to use MySigfox.com service.

To register your device, go to page [https://mysigfox.com/form](https://mysigfox.com/form) and fill in the form:

* _Device ID \(ID zařízení\)_ - Your Device ID
* _Token_ - token you received with your module
* _E-mail_ - mail address you used for order of the module
* _Webhook URL_ - to this address, mysigfox.com will resend every message you send to Sigfox network. POST request will be used

## Changing Webhook URL

If you need to change the Webhook URL after you registered your device, just fill in and send the form again.

## Security

Communication between MySigfox.com and Sigfox Backend is encrypted. Communication between MySigfox.com and your server depends on you. We allow you to use Webhook URL without HTTPS protocol, but we strongly encourage you to use HTTPS only.

{% hint style="info" %}
**You can get free trusted SSL certificate**  
...thanks to the [Let's Encrypt](https://letsencrypt.org/) initiative
{% endhint %}

## Custom POST Parameters

Currently we do not allow to use your own POST parameters to be added to request send by MySigfox.com to your server. If you need to somehow identify requests for particular Sigfox module, you have two options:

1\) you can use _device_ field from message body, which is available in every message sent to your server

2\) or you can add custom query string to the Webhook URL. For example, if your Webhook look like `https://example.cz/endpoint`, you can change it to `https://example.cz/endpoint?foo=bar`. This should deliver your messages without any problem \(but adding your data in the process\).

## POST Request \(message\) Content

Every request we send to your server is JSON encoded message with Content-Type set to `application/json`.

Body of request contains specific fields:

* _snr_ - Signal Noise Ratio
* _device_ - Device ID
* _rssi_ - [Received Signal Strength Indication](https://ask.sigfox.com/questions/2017/snr-rssi.html)
* _time_ - time when the message was received by Sigfox network \(in UNIX timestamp format\)
* _data_ - data sent by your device

## Testing MySigfox.com

To test if everything works as designed, you can use service called [requestb.in](https://requestb.in/) to create temporary storage for http requests.

**Request bin is not wokring right now, but try to google "request bin" and you'll find many similar services like** [**mockbin.org**](http://mockbin.org/) **or** [**postb.in**](https://postb.in/)**.**

### **HOWTO**

1. Go to [https://requestb.in](https://requestb.in/) and press _Create a RequestBin_ button
2. Copy the _Bin URL_ and use it as a Webhook URL
3. Send some testing message from you BigClown setup and refresh the opened requestbin page. Message should appear within 10 seconds after being sent. 

