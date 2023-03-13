# Smart Air Purifier (Project Fornuftig)

Custom PCB based on ESP12-F (ESP8266) wifi module that serves as a smart controller for IKEA Fornuftig Air Purifiers. It's embedded microcontroller enables you to incorporate your device to home automation systems (preferably to Home Assistant) or control it via custom mobile applications as it enjoys support from wide variety of firmwares. This project has been implemented in KiCad (hardware) and in Micropython (sofware).

About IKEA Fornuftig: It's a compact, 31x45 cm air purifier launched in the market around 2020. It effectively cleans the indoor air from harmful PM2.5 particles and pollen for a reasonable price (approx. EUR60). The device is optimised for medium-sized bedrooms and has three fan speed. 

Current status of the development: **Finalized**

Hardware: 
* [x] Schematic
* [x] Layout
* [x] BOM, CPL
* [x] 3D model 
* [x] Testing (v1.1 w/o switch)

Software:
* [x] MicroPython


## Hardware

<img src="https://user-images.githubusercontent.com/44551566/224834081-7d53a183-d076-4745-a9c0-ea1c2188281a.png" width="700" height="400">

PCB is a bit larger than the original one (98x40 mm) with mounting holes placed on it, thus it is supposed to fit just fine inside the plastic housing. Power supply of the fan is +24V, 0.8A. The board has a MC34063DR switching voltage regulator that provides the necessary power (+3v3, avg 70mA, peak >500mA) for the wifi module. This version (v2.0) of the board is designed with a rotary switch. To avoid unnecessary costs and save some space on the board physical filter reset button is not incorporated in this version as this function can be easily achieved through software side. 

The Purifier has a 4-pin PWM fan with +24VDC, 0.5A. The pins are power, ground, clk, fg. Clk is a control pin and fg is the tacho pin for feedback purposes. The fan operates with a constant duty cycle of 50% and variable frequency between ca. 1-300Hz.

MCU programming: the board supports only UART programming via TX, RX pin headers (as no USB interface), thus USB to TTL converter is necessary to upload your firmware. It is recommended to supply the module via VIN and GND pins during initial setup. It is compatible with +5-24V supply (note: in serial bootloader mode you need to supply at least +5V. Standard +3v3 won't work as you may experience some voltage drop via the buck converter so make sure to provide enough voltage during flashing. Supplying +5V won't hurt the ESP as the VIN pin of the board is not directly connected to chip). Boot button is located on the right side of the wifi module.

Tested first version of the board w/o rotary switch:

<img src="https://user-images.githubusercontent.com/44551566/217821551-74f0ebfc-3d94-4d33-9dd0-2dede2cae0c8.jpg" width="700" height="400">

BOM: Most of the chosen components are considered to be basic/standard parts at LCSC, however there are some extended components on the list (two large caps, inductor, esp, jst connectors and uart pin headers).

## Software

The software for Fornuftig has been developed in Micropython. It enables the device to be controlled via mqtt while exploits Home Assistant mqtt autodiscovery features that provides with a smooth (almost zero config) setup process.

More detailed description is available in this repo: https://github.com/horvathgergo/uPurifier

## Contribution

If you find this project useful please support its further development by using the button below:

<a href="https://www.buymeacoffee.com/gergohorvath"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=&slug=gergohorvath&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" /></a>
