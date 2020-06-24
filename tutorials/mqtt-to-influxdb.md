# MQTT to InfluxDB

For storing data from our sensors we like to use `InfluxDB` - time series database. As bridge between MQTT and InfluxDB we created a `mqtt2influxdb`. Service connects to InfluxDB and MQTT broker and by users config subscribe MQTT topics and store data from messages.

## Installation

### Step 1: Install the **MQTT to InfluxDB** service

```text
sudo pip3 install --upgrade mqtt2influxdb
```

### Step 2: Create the `/etc/bigclown` directory

```text
sudo mkdir /etc/hardwario
```

### Step 3: Open the configuration file

{% hint style="info" %}
For text editing, we use **nano** editor. You can save changes by pressing key combination `Ctrl + O` and exit editor by pressing `Ctrl + X`.
{% endhint %}

```text
sudo nano /etc/hardwario/mqtt2influxdb.yml
```

### Step 4: Paste this snippet to the configuration file

{% code title="/etc/hardwario/mqtt2influxdb.yml" %}
```yaml
mqtt:
  host: 127.0.0.1
  port: 1883

influxdb:
  host: 127.0.0.1
  port: 8086
  database: node

points:
  - measurement: temperature
    topic: node/+/thermometer/+/temperature
    fields:
      value: $.payload
    tags:
      id: $.topic[1]
      channel: $.topic[3]

  - measurement: relative-humidity
    topic: node/+/hygrometer/0:4/relative-humidity
    fields:
      value: $.payload
    tags:
      id: $.topic[1]

  - measurement: illuminance
    topic: node/+/lux-meter/0:0/illuminance
    fields:
      value: $.payload
    tags:
      id: $.topic[1]

  - measurement: pressure
    topic: node/+/barometer/0:0/pressure
    fields:
      value: $.payload
    tags:
      id: $.topic[1]

  - measurement: co2
    topic: node/+/co2-meter/-/concentration
    fields:
      value: $.payload
    tags:
      id: $.topic[1]

  - measurement: voltage
    topic: node/+/battery/+/voltage
    fields:
      value: $.payload
    tags:
      id: $.topic[1]

  - measurement: button
    topic: node/+/push-button/+/event-count
    fields:
      value: $.payload
    tags:
      id: $.topic[1]
      channel: $.topic[3]
```
{% endcode %}

{% hint style="info" %}
In the section **tags** you can your identifiers, e.g.: `tags: room: bedroom`
{% endhint %}

### Step 5: Configuration file test

```text
mqtt2influxdb -c /etc/hardwario/mqtt2influxdb.yml --test
```

### Step 6: Start the **MQTT to InfluxDB** service

```text
pm2 start `which python3` --name "mqtt2influxdb" -- `which mqtt2influxdb` -c /etc/bigclown/mqtt2influxdb.yml
```

### Step 7: Save the **PM2 state** \(so it will start after reboot\)

```text
pm2 save
```

{% hint style="info" %}
If you want to see temperature records from database in CSV format, use this command:

`influx -database node -execute "select * from temperature;" -format csv`

Then you must restart the service when you change the configuration file

`pm2 restart mqtt2influxdb`
{% endhint %}

## Configuration file structure and possibilities

In [Step 2](mqtt-to-influxdb.md#step-4-paste-this-snippet-to-the-configuration-file) we paste configuration file, here will be described possibilities in configuration. In configuration you can use [JSONPath](https://goessner.net/articles/JsonPath/). For example in in measurement you can identify tag id from MQTT topic by syntax `$.topic[1]` as you can see in [Step 4](mqtt-to-influxdb.md#step-4-paste-this-snippet-to-the-configuration-file).

### MQTT

MQTT part of configuration file is where you define connection to MQTT broker. `mqtt2influxdb` supports secured connection! This section is **required**.

```yaml
mqtt:
  host: MQTT Broker adress (required)
  port: MQTT Broker port (required)
  username: Username to secured MQTT broker (optional)
  password: Users password to secured MQTT broker (optional)
  cafile: CA to secured MQTT broker (optional)
  certfile: Certificate to secured MQTT broker (optional)
  keyfile: Certificate Key file to secured MQTT broker (optional)  
```

### HTTP

You can define web hooks so data can be posted to your endpoint. This section is **optional**.

```yaml
http:
  destination: Endpoint url (required)
  action: Request type (required)
  username: Username for secured request (optional)
  password: Password for secured request (optional)
```

### InfluxDB

Important part of config is of course definition of InfluxDB connection. This section is **required**.

```yaml
influxdb:
  host: InfluxDB adress (required)
  port: InfluxDB port (required)
  database: Database name (required)
  username: Username to InfluxDB (optional)
  password: Users password to InfluxDB (optional)
  ssl: SSL connection (optional)
```

### Base64 Decode

Decode base64 messages. This section is **optional**.

```yaml
base64decode:
  source: base64 coded message (required)
  target: encoded message (required)
```

### Points

Points section is where you define messages you want to store in database. This section is **required**.

```yaml
points:
  measurement: Measurement name in database (required)
  topic: Define MQTT topic where messages are posting to (required)
  httpcontent: Define payload in http request if filled in HTTP chapter (optional)
  fields:
    value: Value field in InfluxDB (required)
    type: Variable type (required)
    
```

#### Tags

Tags are for identification measurement in database. This section is **optional**.

```yaml
tags:
  id: ID field in InfluxDB (optional)
```

#### Database

For every measurement you can define specific database name. This field is **optional**.

```yaml
database: Specific database to store measurement (optional)
```

