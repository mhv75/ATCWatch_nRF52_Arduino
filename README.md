# Arduino Core for ATC nRF52 Boards [Adafruit nRF52 Arduino](https://github.com/adafruit/Adafruit_nRF52_Arduino)

[![Build Status](https://github.com/mhv75/ATCWatch_nRF52_Arduino/workflows/Build/badge.svg)](https://github.com/mhv75/ATCWatch_nRF52_Arduino/actions)

This repository contains the Arduino BSP for Hackable nRF52 Smart Watch series using by [@ATC1441](https://github.com/atc1441)'s [DaflasherFiles](https://github.com/atc1441/DaFlasherFiles) to enable flashing a custom [Arduino firmware](https://github.com/atc1441/ATCwatch) to them. 

## BSP Installation

There are two methods that you can use to install this BSP. We highly recommend the first option unless you wish to participate in active development of this codebase via Github.

### Recommended: ATCWatch nRF52 BSP via the Arduino Board Manager

 1. [Download and install the Arduino IDE](https://www.arduino.cc/en/Main/Software) (At least v1.6.12)
 2. Start the Arduino IDE
 3. Go into Preferences
 4. Add https://mhv75.github.io/arduino-board-index/package_atcwatch_index.json as an 'Additional Board Manager URL'
 5. Restart the Arduino IDE
 6. Open the Boards Manager from the Tools -> Board menu and install 'ATCWatch nRF52 by mhv75'
 7. Once the BSP is installed, select a board from the Tools -> Board menu, which will update your system config to use the right compiler and settings for the nRF52.


### Adafruit's nrfutil tools

[adafruit-nrfutil](https://github.com/adafruit/Adafruit_nRF52_nrfutil) (derived from Nordic [pc-nrfutil](https://github.com/NordicSemiconductor/pc-nrfutil)) is needed to upload sketch via serial port.

- For Windows and macOS, pre-built executable binaries are included in the BSP at `tools/adafruit-nrfutil/`. It should work out of the box.
- Linux user need to run follow command to install it from PyPi

```
$ pip3 install adafruit-nrfutil --user
```





### Burning new Bootloader

To burn the bootloader you will need the following tools installed
on your system and available in the system path:

- Segger [JLink Software and Documentation Pack](https://www.segger.com/downloads/jlink)
- Nordic [nRF5x Command Line Tools](https://www.nordicsemi.com/Software-and-Tools/Development-Tools/nRF-Command-Line-Tools)

Check to make sure you can run `nrfjprog` from your terminal/command prompt

**macOS Note** At present, you will need to create a symlink in `/usr/local/bin` to the
`nrfjprog` tool wherever you have added it. You can run the following command, for example:

```
$ ln -s $HOME/prog/nordic/nrfjprog/nrfjprog /usr/local/bin/nrfjprog
```

Once the tools above have been installed and added to your system path:



## Credits
This would not have been possible to do without the excellent work of @atc1441 and many more of the hackers who joined him in hacking nrf watches..
This core is based on [Arduino-nRF5](https://github.com/sandeepmistry/arduino-nRF5) by Sandeep Mistry,
which in turn is based on the [Arduino SAMD Core](https://github.com/arduino/ArduinoCore-samd).

The following libraries are used:

- [FreeRTOS](https://www.freertos.org/) as operating system
- [LittleFS](https://github.com/ARMmbed/littlefs) for internal file system
- [nrfx](https://github.com/NordicSemiconductor/nrfx) for peripherals driver
- [TinyUSB](https://github.com/hathach/tinyusb) as usb stack
