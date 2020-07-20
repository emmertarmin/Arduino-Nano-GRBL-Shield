# Arduino-Nano-GRBL-Shield
This CNC Shield was designed to replace a "Stepper Bricklet" from Tinkerforge. It is much larger in size, but the four screw holes are compatible in size and placement.

## Features
- 102mm x 50mm
- Arduino Nano pinout is designed for GRBL firmware.
- 3 individual "X-Y-Z" stepper drivers, with a fourth "A" Axis whose `step` and `dir` pins can be coupled with either of the other three axes.
- Limit switches per axis are connected in series for NC switch operation. This means the Arduino is going to expect a closed circuit on all 6 switches (if switches are enabled in the firmware) and interpret an open circuit as a triggered switch.
- Switches have RC circuits as is [recommended by GRBL](https://github.com/gnea/grbl/wiki/Wiring-Limit-Switches) for noise filtering. These SMD parts can be left unpopulated.
- 12V Barrel Jack power source for stepper motors.
- If Arduino is to be driven without an active USB connection, the 12V source is to be stepped down to 6-7 Volts with a switching regulator. I used [this DSN-1504 one](https://www.hestore.hu/prod_10038118.html?lang=en) from Hestore.
- The only smd parts that are needed for operation are one 10k pullup resistor on the `EN` pin under the Arduino, and 12 pieces of 100k pulldown resistors right next to the stepper drivers, which control `MS1-MS3` pins to set microstepping.

> Please make sure your Arduino Nano can handle an external 6-7V source on VIN and an active USB connection simultaneously. Officially it should be able to do that, but there's stories on the internet about versions of Nanos that got burnt.

> Also, while a direct 12V source on the VIN of the Arduino is officially fine, it's not recommended, as the internal regulator of the Arduino will dissipate the 7V difference in form of heat. This is why I used a switching step-down converter.

## Images

Renders were created with [tracespace.io](https://tracespace.io/)

![Top](https://github.com/emmertarmin/Arduino-Nano-GRBL-Shield/blob/master/images/top.svg?raw=true)

![Bottom](https://github.com/emmertarmin/Arduino-Nano-GRBL-Shield/blob/master/images/bottom.svg?raw=true)

The images below show an earlier version which lacked the RC filters. Apart from that it's the same. Please excuse the dusty Nano.

![Front](https://github.com/emmertarmin/Arduino-Nano-GRBL-Shield/blob/master/images/front.jpg?raw=true)

![Side](https://github.com/emmertarmin/Arduino-Nano-GRBL-Shield/blob/master/images/side.jpg?raw=true)
