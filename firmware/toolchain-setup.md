# Toolchain Setup

In this document we will describe the installation of tools for working with firmware - the firmware toolchain. The toolchain is designed to allow the firmware operations on all the supported operating systems using a command line in a **uniform manner**.

{% hint style="info" %}
Orientation on a command line interface has the advantage to build your firmware automatically on server, e.g. on commit to GitHub via Travis CI continuous integration service.
{% endhint %}

The firmware toolchain consists of several fundamental components:

* Compiler **GCC ARM Embedded**
* Version control system **Git**
* Interpret for scripting language **Python 3**
* DFU upload utility **dfu-util**
* Program **BigClown Firmware Tool**

At the end of the article, we'll show how to develop and compile firmware with popular editors like **Atom** or **Visual Studio Code**.

To install, go to one of the supported platforms:

* [**Setup on Windows**](toolchain-setup.md#setup-on-windows)
* [**Setup on macOS**](toolchain-setup.md#setup-on-macos)
* [**Setup on Ubuntu**](toolchain-setup.md#setup-on-ubuntu)
* [**Setup on Generic Linux**](toolchain-setup.md#setup-on-generic-linux)

To upgrade an existing installation, go to one of the supported platforms:

* [**Update on Windows**](toolchain-setup.md#update-on-windows)
* [**Update on macOS**](toolchain-setup.md#update-on-macos)
* [**Update on Ubuntu**](toolchain-setup.md#update-on-ubuntu)
* [**Update on Generic Linux**](toolchain-setup.md#update-on-generic-linux)

## Setup on Windows

{% hint style="warning" %}
You will need administrator rights to install.
{% endhint %}

### Step 1: Download the current version of the **BigClown Toolchain** Windows installer

[Download from GitHub](https://github.com/bigclownlabs/bch-windows-toolchain/releases)

### Step 2: Launch the downloaded installer and choose the destination directory

![](../.gitbook/assets/_firmware_toolchain-setup_windows-location.png)

### Step 3: Now you can adjust the desired **Path** environment variable \(we recommend to leave the default settings if in doubt\) and proceed with the installation

![](../.gitbook/assets/_firmware_toolchain-setup_windows-paths.png)

### Step 4: The FTDI driver setup will launch automatically during the installation - install it

![](../.gitbook/assets/_firmware_toolchain-setup_windows-ftdi.png)

### Step 5: After finishing the installation, lauch the **BigClown Toolchain** using one these 3 ways

* From the **Desktop**
* From the **Start** menu
* From the **context menu** on the selected directory \(using a right click\)

{% hint style="info" %}
The advantage of the context menu is to open the **BigClown Toolchain** directly in the directory location you need to work with.
{% endhint %}

![](../.gitbook/assets/_firmware_toolchain-setup_windows-toolchain.png)

### Step 6: Continue on the document [**Toolchain Guide**](toolchain-guide.md). You may also try

* [**Integration with Visual Studio Code**](toolchain-setup.md#integration-with-visual-studio-code)

## Update on Windows

* Download and install the new version according to the chapter [**Setup on Windows**](toolchain-setup.md#setup-on-windows).

## Uninstall on Windows

Uninstall **Apps & features**:

![](../.gitbook/assets/_firmware_toolchain-setup_windows-uninstall.png)

## Setup on macOS

{% hint style="warning" %}
The following procedure has been tested on **macOS 10.12**.
{% endhint %}

### Step 1: Open the **Terminal** application

### Step 2: Install [**Homebrew**](https://brew.sh/) \(unless you already have it\)

{% hint style="info" %}
Homebrew is the package management system and the ecosystem of packages for macOS.
{% endhint %}

### Step 3: Install **GCC ARM Embedded**

```text
brew tap armmbed/formulae
```

```text
brew install armmbed/formulae/arm-none-eabi-gcc
```

### **Step 4:** Install **Git**

```text
brew install git
```

### **Step 5:** Install **dfu-util**

```text
brew install dfu-util
```

### **Step 6:** Install **Python 3**

```text
brew install python3
```

### **Step 7:** Update **pip** \(Python Package Manager\) to the latest version

```text
sudo pip3 install --upgrade --no-cache-dir pip
```

### Step 8: Install **BigClown Firmware Tool**

```text
sudo pip3 install --upgrade --no-cache-dir bcf
```

### **Step 9:** Continue on the document [**Toolchain Guide**](https://www.bigclown.com/doc/firmware/toolchain-guide/). You may also try

* [**Integration with Visual Studio Code**](https://www.bigclown.com/doc/firmware/toolchain-setup/#integration-with-visual-studio-code)

## Update on macOS

* Update of packages:

```text
brew update && brew upgrade
```

* BigClown Firmware tool update:

```text
sudo pip3 install --upgrade --no-cache-dir bcf
```

## Setup on Ubuntu

{% hint style="warning" %}
The following procedure has been tested on **Ubuntu 18.04.1 LTS**.
{% endhint %}

### Step 1: Open the **Terminal** application

### Step 2: Add the following PPA to the list of available repositories

```text
sudo add-apt-repository ppa:team-gcc-arm-embedded/ppa
```

### Step 3: Update the index of the available packages

```text
sudo apt update
```

### Step 4: Install compiler & necessary tools

```text
sudo apt install gcc-arm-embedded git dfu-util python3.5 python3-pip python3-setuptools
```

### Step 5: Update **pip** \(Python Package Manager\) to the latest version

```text
sudo pip3 install --upgrade --no-cache-dir pip
```

### Step 6: Install **BigClown Firmware Tool**

```text
sudo pip3 install --upgrade --no-cache-dir bcf
```

### Step 7: Add user to **dialout** group

```text
sudo adduser $USER dialout
```

### Step 11: Continue on the document [**Toolchain Guide**](https://www.bigclown.com/doc/firmware/toolchain-guide/). You may also try:

* [**Integration with Visual Studio Code**](toolchain-setup.md#integration-with-visual-studio-code)

## Update on Ubuntu

* Update of packages:

```text
sudo apt update && sudo apt upgrade
```

* BigClown Firmware tool update:

```text
sudo pip3 install --upgrade --no-cache-dir bcf
```

## Setup on Generic Linux

If you have other Linux distribution or unsupported Ubuntu version, we recommend to use official _GNU Embedded Toolchain for ARM_ from [developer.arm.com](https://developer.arm.com/) pages. This package is validated by ARM and tested by us.

### Step 1: Go to [https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads) and download **Linux 64-bit** package

### Step 2: Extract package to filesystem, e.g. into `/opt` folder \(_available for all users, you will need root privileges_\) or into `~/.local/opt` folder \(_available only for you_\)

#### **Step 1: /opt version**

```text
cd <folder with package> # go to folder with downloaded file
sudo cp gcc-arm-none-eabi-6-*-update-linux.tar.bz2 /opt  # copy to destination folder
cd /opt  # go there
sudo tar xjf gcc-arm-none-eabi-6-*-update-linux.tar.bz2  # unpack file
```

#### Step 3: **~/.local/opt version**

```text
mkdir -p ~/.local/opt  # create folder
cd <folder with package> # go to folder with downloaded file
cp gcc-arm-none-eabi-6-*-update-linux.tar.bz2 ~/.local/opt  # copy to destination folder
cd ~/.local/opt  # go there
tar xjf gcc-arm-none-eabi-6-*-update-linux.tar.bz2  # unpack file
```

### Step 3: Create a symbolic link `gcc-arm-none-eabi-6`

```text
sudo ln -s gcc-arm-none-eabi-6-<version>-update gcc-arm-none-eabi-6  # where <version> could be: 2017-q2
```

### Step 4: Update `PATH` variable so you can use arm-none-eabi-\* binaries directly

```text
cd  # go to user home folder
# use your favorite editor and edit ".profile" file
# find line with PATH variable. e.g.:

    export PATH="$PATH:/…"
```

{% hint style="warning" %}
Please note that three dots \(…\) represents some text there.
{% endhint %}

```text
# and add to your path to the end (/opt version):

export PATH="$PATH:/…:/opt/gcc-arm-none-eabi-6/bin"

# or (~/.local/opt version)

export PATH="$PATH:/…:~/.local/opt/gcc-arm-none-eabi-6/bin"

# if there is no PATH line, add it

export PATH="$PATH:/opt/gcc-arm-none-eabi-6/bin"

# or

export PATH="$PATH:~/.local/opt/gcc-arm-none-eabi-6/bin"
```

### Step 5: Use your distribution package manager and install

* **Git**
* **Python 3**
* **dfu-util**

### Step 6: Install **BigClown Firmware Tool**

```text
sudo pip3 install --upgrade --no-cache-dir bcf
```

### Step 7: Continue on the document [**Toolchain Guide**](toolchain-guide.md). You may also try

* [**Integration with Visual Studio Code**](toolchain-setup.md#integration-with-visual-studio-code)

## Update on Generic Linux

* Update **Toolchain**
  * Download updated **Linux 64-bit** package from [https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads](https://developer.arm.com/open-source/gnu-toolchain/gnu-rm/downloads)
  * Extract it into proper folder \(`/opt`, `~/.local/opt` or other\)
  * Update symbolic link

```text
sudo ln -sf gcc-arm-none-eabi-6-<version>-update gcc-arm-none-eabi-6  # where <version> could be: 2017-q2
```

or

```text
ln -sf gcc-arm-none-eabi-6-<version>-update gcc-arm-none-eabi-6  # where <version> could be: 2017-q2
```

* Update packages
  * Use your distribution package manager
* BigClown Firmware tool update:

```text
sudo pip3 install --upgrade bcf
```

## Integration with Visual Studio Code

Every BigClown project contains `.vscode` configuration folder so you just open the project folder in **Visual Studio Code** and you're ready to go.

We also suggest to install [C/C++ Intellisense and debug extentsion from Microsoft](https://marketplace.visualstudio.com/items?itemName=ms-vscode.cpptools).

In file `.vscode/tasks.json` there are some tasks which you can run by pressing `Ctrl+P`and typing `task`.

| ask | Description |
| :--- | :--- |
| build | Build active project |
| clean | Clean active project |
| dfu | Flash compiled firmware with dfu-util to the Core Module |
| ozone | Run Ozone debugger which can be used with J-Link debugger |
| update | Update SDK folder/submodule to the latest version |

{% hint style="info" %}
Project make file allows quicker parallel compilation. This can be set in `.vscode/tasks.json` where you set `"args": ["-j4"],` parameter, where the number 4 is the number of your CPU cores.
{% endhint %}

## Integration with J-Link debugger

To debug the running code on Core Module you can use Ozone debugger with J-Link debug probe. It is also possible to use GDB/OpenOCD with other debug probes but this is not documented yet.

Download the [Ozone debugger](https://www.segger.com/downloads/jlink#Ozone).

{% hint style="info" %}
**For Windows users:** Ozone folder also needs to be set in `PATH` environment variable or you can simply edit `Makefile` and set absolute path to the `Ozone.exe` file. It is also possible to open project directly in **Ozone**, please see the options below.
{% endhint %}

How to start debugging the project:

* In the **command line** by typing `make ozone`
* In **Visual Studio Code** by pressing `F5` or `Ctrl+P` and typing `task ozone`
* In **Ozone** by loading project configuration file `sdk/tools/ozone/ozone.jdebug`.

## Related Documents

* [**Toolchain Guide**](toolchain-guide.md)

