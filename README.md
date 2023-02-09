# Smart Air Purifier (Project Fornuftig)

Custom PCB based on ESP12-F (ESP8266) wifi module that serves as a smart controller for IKEA Fornuftig Air Purifiers. It's embedded microcontroller enables you to incorporate your device to home automation systems (preferably to Home Assistant) or control it via custom mobile applications as it enjoys support from wide variety of firmwares. This project is going to be implemented in two major phases: Hardware and Software design. Hardware is designed with KiCAD, will be manufactured with assembly services by a chosen reputable Chinese company. Software is planned to be based on MicroPython and ESPHome firmwares.

About IKEA Fornuftig: It's a compact, 31x45 cm air purifier launched in the market around 2020. It effectively cleans the indoor air from harmful PM2.5 particles and pollen for a reasonable price (approx. EUR60). The device is optimised for medium-sized bedrooms and has three fan speed. 

Current status of the development: **Prototype is ready and under testing**

Hardware: 
* [x] Schematic
* [x] Layout
* [x] BOM, CPL
* [x] 3D model 
* [ ] Testing

Software:
* [ ] ESPHome
* [ ] MicroPython


## Hardware

<img src="https://user-images.githubusercontent.com/44551566/215624237-50fa134a-c428-43b6-a8c3-364afe3d16e4.png" width="700" height="400">

PCB has the same size as the original one (90x40 mm) with mounting holes placed on it, thus it is supposed to fit just fine inside the plastic housing. Power supply of the fan is +24V, 0.8A. The board has a MC34063DR switching voltage regulator that provides the necessary power (+3v3, >500mA) for the wifi module. This version of the board is designed without a rotary switch. Furthermore in order to avoid unnecessary costs and save some space on the board physical filter reset button is not incorporated in this version as this function can be easily achieved through software side. 

The Purifier has a 4-pin PWM fan with +24VDC, 0.5A. The pins are power, ground, pwm, fg. PWM is a control pin for pulse width modulation and FG is the tacho pin for feedback purposes.

MCU programming: the board supports only UART programming via TX, RX pin headers (as no USB interface), thus USB to TTL converter is necessary to upload your firmware. It is recommended to supply the module via VIN and GND pins during initial setup. It is compatible with +5-24V supply (note: in serial bootloader mode you need to supply at least +5V. Standard +3v3 won't work as you may experience some voltage drop via the buck converter so make sure to provide enough voltage during flashing. Supplying +5V won't hurt the ESP as the VIN pin of the board is not directly connected to chip). Boot button is located on the right side of the wifi module.

BOM: Most of the chosen components are considered to be basic/standard parts at LCSC, however there are some extended components on the list (two large caps, inductor, esp, jst connectors and uart pin headers).

## Contribution

If you find this project useful please support its further development by using the button below:

<a href="https://www.buymeacoffee.com/gergohorvath"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=&slug=gergohorvath&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff" /></a>
