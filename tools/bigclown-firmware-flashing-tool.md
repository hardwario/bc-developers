# HARDWARIO firmware flashing tool

This multi-platform Python tool can flash [Radio Dongle](https://shop.bigclown.com/radio-dongle) and [Core Module](https://shop.bigclown.com/core-module) with local binary or latest released firmwares from GitHub.

The installation and usage instructions are in the [**Quick Tutorial**](../tutorials/quick-tutorial.md) and **Projects** section.

## Install & Upgrade

You can install tools with `pip3` python tool. Always make sure that you are using the latest version.

```text
sudo pip3 install --upgrade --no-cache-dir bcf
```

### Autocomplete

For Ubuntu/Linux you can enable autocomplete. Add this line to `~/.bashrc`

```text
eval "$(_BCF_COMPLETE=source bcf)"
```

Then run this command to reload .bashrc

```text
source ~/.bashrc
```

Now you can for example write `bcf --de`, press TAB key and `--device` text is automatically completed.

## Usage examples

Update and dowload list of all firmwares from GitHub

```text
bcf update
```

List all firmwares

```text
bcf list
```

Search for firmware

```text
bcf search button
```

Flash Core Module **R2**

```text
bcf flash bigclownlabs/bcf-radio-push-button:latest
```

{% hint style="info" %}
You can use optional `--device` parameter to choose the right serial port. This way the `bcf` won't ask you every time.
{% endhint %}

Flash Core Module **R1**

```text
bcf flash --device dfu bigclownlabs/bcf-radio-push-button:latest
```

Flash **Radio Dongle** with latest firmware

```text
bcf flash --device /dev/ttyUSB0 bigclownlabs/bcf-gateway-usb-dongle:latest
```

### `bcf` logging

It is possible to use `bcf` as a serial console to see log messages which are printed with `bc_log_`APIs. It is using serial port in the parameter and 115200 baud speed with 8N1 uart format.

```text
bcf log --device [device]
```

Flash firmware and immediatelly start logging after upload

```text
bcf flash --device [device] [firmware]:[version] --log
```

Reset Core Module and immediatelly start logging after upload

```text
bcf reset --device [device] --log
```

### `bcf --help` <a id="bcf-help"></a>

```text
hub@hpnix:~$ bcf --help
usage: bcf [-h] [-v] COMMAND ...

BigClown Firmware Tool

positional arguments:
  COMMAND
    update       update list of available firmware
    list         list firmware
    flash        flash firmware
    devices      show devices
    search       search in firmware names and descriptions
    pull         pull firmware to cache
    clean        clean cache
    create       create new firmware
    read         download firmware to file
    log          show log
    reset        reset core module, not work for r1.3
    help         show help

optional arguments:
  -h, --help     show this help message and exit
  -v, --version  show program's version number and exit
```

