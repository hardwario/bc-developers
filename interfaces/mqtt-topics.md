# MQTT topics

## Generic Node Topics

Detailed list of topics is in **README** in GitHub repository [**bcf-generic-node**](https://github.com/bigclownlabs/bcf-generic-node).

### Firmware

| Explanation | MQTT Topic | Payload |
| :--- | :--- | :--- |
| Firmware info | node/{id}/info | `{"firmware": "motion-detector", "version": "v1.3.0"}` |

### Battery

| Explanation | MQTT Topic | Payload |
| :--- | :--- | :--- |
| Battery Module voltage | node/{id}/battery/standard/voltage | 3.12 |
| Mini Battery Module voltage | node/{id}/battery/mini/voltage | 6.21 |

### Sensors

| Explanation | MQTT Topic |
| :--- | :--- |
| Illuminance | node/{id}/lux-meter/0:0/illuminance |
| Relative humidity | node/{id}/hygrometer/0:2/relative-humidity |
| Pressure | node/{id}/barometer/0:0/pressure |
| Altitude | node/{id}/barometer/0:0/altitude |
| Temperature | node/{id}/thermometer/0:1/temperature |
| CO2 meter | node/{id}/co2-meter/-/concentration |

### Relays

Allowed values for payload are `true`/`false`

| Explanation | MQTT Topic | Response |
| :--- | :--- | :--- |
| Power Module relay set | node/{id}/relay/-/state/set | `node/{id}/relay/-/state` |
| Power Module relay get | node/{id}/relay/-/state/get | `node/{id}/relay/-/state` |
| Relay Module | node/{id}/relay/0:0/state/set | `node/{id}/relay/0:0/state` |
| Relay Module get | node/{id}/relay/0:0/state/get | `node/{id}/relay/0:0/state` |
| Relay Module pulse | node/{id}/relay/0:0/pulse/set | `{"duration":200, "direction":true}` |

### LED

| Explanation | MQTT Topic |
| :--- | :--- |
| LED on the Core Module | `node/{id}/led/-/state/set` |

### **Button**

| Explanation | MQTT Topic |
| :--- | :--- |
| Button press | `node/{id}/push-button/-/event-count` |

### **PIR**

| Explanation | MQTT Topic |
| :--- | :--- |
| Object movement detection | `node/{id}/pir/-/event-count` |

### **LED Strip**

| Explanation | MQTT Topic / explanation | **Example** |
| :--- | :--- | :--- |
| Set brightness 0-100% | `node/{id}/led-strip/-/brightness/set` |  |
| Set color "\#250000" or RGBW "\#250000\(80\)" | `node/{id}/led-strip/-/color/set` |  |
| Set compound | `node/{id}/led-strip/-/compound/set` | `[20, "#ff0000", 20, "#00ff00"]` |
| Set effect | `node/{id}/led-strip/-/effect/set` | `{"type":"test"}` |
|  |  | `{"type":"rainbow", "wait":50}` |
|  |  | `{"type":"rainbow-cycle", "wait":50}` |
|  |  | `{"type":"theater-chase-rainbow", "wait":50}` |
|  |  | `{"type":"color-wipe", "wait":50, "color":"#800000"}` |
|  |  | `{"type":"theater-chase", "wait":50, "color":"#008000"}` |
|  |  | `{"type":"stroboscope", "wait":50, "color":"#0000ff"}` |
|  |  | `{"type":"icicle", "wait":50, "color":"#ff0000"}` |
|  |  | `{"type":"pulse-color", "wait":200, "color":"#ff0000"}` |
| Thermometer effect | `node/{id}/led-strip/-/thermometer/set` | `{"temperature": 22.5, "min":-20, "max": 50}` |
|  | turn on "backlight" \(0-255\) | `{"temperature": 22.5, "min":-20, "max": 50, "white-dots": 10}` |
|  | display a set point pixel with a selected color | `{"temperature": 22.5, "min":-20, "max": 50, "set-point": 30, "color":"#ff0000"}` |
|  |  | `{"temperature": 22.5, "min":-20, "max": 50, "white-dots": 10, "set-point": 30, "color":"#ff0000"}` |
|  | display only set-point | `{"temperature": -20, "min":-20, "max": 50, "set-point": 30, "color":"#00ff00"}` |

### **LCD Module**

| **Explanation** | MQTT Topic | Response |
| :--- | :--- | :--- |
| left button | `node/{id}/push-button/lcd:left/event-count` |  |
| right button | `node/{id}/push-button/lcd:right/event-count` |  |
| clear screen | `node/{id}/lcd/-/screen/clear` |  |
| write text | `node/{id}/lcd/-/text/set` | `{"x": 5, "y": 10, "text": "BigClown"}` |
|  |  | `{"x": 5, "y": 40, "text": "BigClown", "font": 28}` |

## Gateway Topics

Detailed list of topics is in **README** in GitHub repository [**bch-gateway**](https://github.com/bigclownlabs/bch-gateway)

{% hint style="info" %}
Replace `{id}` with **id** or **name** of gateway, use "all" for request to all.  
Also to see the MQTT responses open the Node-RED debug tab or run this console command `mosquitto_sub -t gateway/#`.
{% endhint %}

### Pairing

| Explanation | MQTT Topic | **Response** |
| :--- | :--- | :--- |
| start | `gateway/{id}/pairing-mode/start` | `gateway/{id}/pairing-mode` `"start"` |
| stop | `gateway/{id}/pairing-mode/stop` | `gateway/{id}/pairing-mode` `"stop"` |

### **Paired nodes**

| **Explanation** | MQTT Topic | Response |
| :--- | :--- | :--- |
| list | `gateway/{id}/nodes/get` | `gateway/{id}/nodes [{"id": "a7c8b05762dd", "alias": "generic-node:0"},  {"id": "836d1983718a", "alias": "lcd-thermostat:0"}]` |
| purge all nodes | `gateway/{id}/nodes/purge` | `gateway/{id}/nodes` `[]` |

### **Manual add/remove**

| **Explanation** | MQTT Topic | Response |
| :--- | :--- | :--- |
| add | `gateway/{id}/nodes/add`  `"{id-node}"` | `gateway/{id}/attach` `"{id-node}"` |
| remove | `gateway/{id}/nodes/remove`  `"{id-node}"` | `gateway/{id}/detach` `"{id-node}"` |

### Aliases

| Explanation | MQTT Topic |
| :--- | :--- |
| set | `gateway/{id}/alias/set` `{"id": "id-node", "alias": "new-name"}` |
| remove | `gateway/{id}/alias/remove`  `"{id-node}"` |
| remove alias | `gateway/{id}/alias/set`  `{"id": "id-node", "alias": null}` |

### Scan wireless

| Explanation | MQTT Topic | Response |
| :--- | :--- | :--- |
| start | ~~`gateway/{id}/scan/start`~~ | `gateway/{id}/scan` `"start"` |
|  | found node | `gateway/{id}/found` `"{id-node}"` |
| stop | `gateway/{id}/scan/stop` | `gateway/{id}/scan` `"stop"` |

## Mosquitto command examples

Send to all connected gateways:

```text
mosquitto_pub -t gateway/all/pairing-mode/start -n
```

```text
mosquitto_pub -t gateway/all/pairing-mode/stop -n
```

```text
mosquitto_pub -t gateway/all/nodes/get -n
```

```text
mosquitto_pub -t gateway/all/nodes/purge -n
```

Gateway named _"usb-dongle"_:

```text
mosquitto_pub -t gateway/usb-dongle/pairing-mode/start -n
```

```text
mosquitto_pub -t gateway/usb-dongle/pairing-mode/stop -n
```

Gateway named _"core-module"_:

```text
mosquitto_pub -t gateway/core-module/pairing-mode/start -n
```

```text
mosquitto_pub -t gateway/core-module/pairing-mode/stop -n
```

