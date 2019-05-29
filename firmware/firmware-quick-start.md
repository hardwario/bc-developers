# Firmware Quick Start

You can easily edit or create your own custom firmware for BigClown on Windows, Linux or macOS. This guide will show you in a few steps how to start.

## Windows

1. Install [VSCode IDE](https://code.visualstudio.com/) first
2. Install BigClown Toolchain on [Windows](toolchain-setup.md#setup-on-windows), keep the default install options if in doubt
3. Create BigClown folder where all your BigClown projects will be located
4. Right click on that folder and choose Open with BigClown Toolchain
5. Create a new project skeleton by typing `bcf create my_project`
6. Go to the new created folder by typing `cd my_project`
7. Run VSCode by typing `code .` \(note the dot "."\)
8. Your application code is in file `app/application.c`
9. Build firmware by pressing `Ctrl + Shift + B`, VSCode may ask in the bottom right corner if you would like to use different Shell. Confirm that and try to build project again.
10. Connect Core Module and flash the firmware by pressing Ctrl + P and typing task flash. In the terminal window the flasher will ask for COM port, if you have just one, type zero `0` and press Enter
11. The Core Module is flashed. The red LED will turn on, when you press the button the LED toggles.



