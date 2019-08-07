<<<<<<< HEAD
# efm8-arduino-programmer
Program EFM8 devices using an Arduino Mega.

Thanks to jaromir-sukuba and racerxdl for working on firmware to implement C2 protocol via arduino GPIO.  This work largely pulls from them.

## Pre-Steps
Currently, it is for Arduino Mega and maps C2D and C2CK to digital pins 2 and 3, respectively. 

C2 is a 2-pin protocol.  Any arduino should work to implement the protocol via GPIO.  Just need to make sure that the correct pins are mapped for your Arduino.
=======
# Setting up

C2 is a 2-pin protocol.  Any arduino should work to implement the protocol via GPIO.  Just need to make sure that the correct pins are mapped for your Arduino.  Check the [firmware file Arduino Mega](https://github.com/christophe94700/efm8-arduino-programmer/blob/master/prog/arduino_mega.ino#L11) or [firmware file Arduino Uno](https://github.com/christophe94700/efm8-arduino-programmer/blob/master/prog/arduino_uno.ino#L11) and change the pins to map to your device if needed.  Currently, it is:
- for Arduino Mega and maps C2D and C2CK to digital pins 2 and 3, respectively.
- for Arduino Uno and maps C2D and C2CK to digital pins 5 and 6, respectively.
>>>>>>> efm8-arduino-programmer/master

### Update Pins
Check the [firmware file](https://github.com/conorpp/efm8-arduino-programmer/blob/master/prog/prog.ino#L11) and change the pins to map to your device if needed.

### Arduino Uno support
To use it for Arduino Uno you can just swap from E to D. Just replace all `PORTE`, `DDRE` and `PINE` with `PORTD`, `DDRD` and `PIND`. You can read about Port Registers here: https://www.arduino.cc/en/Reference/PortManipulation

### Write firmware to Arduino
Program the firmware to the arduino and connect C2D, C2CK, and GND to your target device.
<<<<<<< HEAD

## Setup for flashing EFM8
It is set up in a client/server model to be able to easily support programming multiple targets at the same time.
=======
# Firmware
For RF Bridge [RF_Bridge](https://github.com/christophe94700/efm8-arduino-programmer/blob/master/Firmware/RF_Bridge.hex)
For Test blinking blue Led [Blinky Led](https://github.com/christophe94700/efm8-arduino-programmer/blob/master/Firmware/Blinky_Led.hex)
# Software
>>>>>>> efm8-arduino-programmer/master

### Requirements
- You need to have Python (2.7) installed.
- Then, install some required python modules.

Use Python 2.7 and Pyserial for [flash27.py](https://github.com/christophe94700/efm8-arduino-programmer/blob/master/flash27.py)
Version Select a serial speed  [SeepdFlash27.py](https://github.com/christophe94700/efm8-arduino-programmer/blob/master/SeepdFlash27.py)

Use Python 3.6 and Pyserial for [flash36.py](https://github.com/christophe94700/efm8-arduino-programmer/blob/master/flash36.py)
Version Select a serial speed  [SeepdFlash36.py](https://github.com/christophe94700/efm8-arduino-programmer/blob/master/SeepdFlash36.py)

Version executable Windows standalone   [flash27_EXE.zip](https://github.com/christophe94700/efm8-arduino-programmer/blob/master/ExeForWindows/flash27_EXE.zip))

```
pip install -r requirements.txt
```

<<<<<<< HEAD
### Setup of Server & Client

#### Server 
First you must run the server that will handle communication to the arduino.
=======
# Running

Programming one target.
>>>>>>> efm8-arduino-programmer/master

```
python flash.py <serial-port> <firmware.hex>
```

<<<<<<< HEAD
Supply a list of serial ports (you can use more than one Arduino at a time) to handle programming.  E.g /dev/USB1 or COM1 or /dev/cu.usbmodem*.

#### Client
Then you can finally program something using the client script.

```
python prog_client.py <serial-port> <firmware.hex>
```

This will connect to the server and tell it to download specified firmware via specified arduino.

## Troubleshooting

- If your server can't start make sure you have port 4040 available
- If you get python errors make sure you're not running python3
- Some modules need sudo on some systems
- If you're getting data errors, reduce baud rate: https://github.com/conorpp/efm8-arduino-programmer/issues/5
=======
Example for Linux: 
```flash27.py /dev/ttyACM0 RF_Brige.hex```
or 
```sudo flash27.py /dev/ttyACM0 RF_Brige.hex```

Example for Windows: ```python flash27.py COM8 RF_Bridge.hex```
## Select a serial speed
`python SeepdFlash27.py Com8 1000000 RF_Bridge.hex`
## Windows standalone
Unzip the ZIP archive flash27_EXE.zip.

`flash27.exe com8 f:\test\RF_Bridge.hex`

# Troubleshooting

- Some modules need sudo on some systems

# Changing the communication speed


Edit the following lines:
In the Python program modify the following line to switch to a speed of 115200baud / sec:

    self.ser = serial.Serial (com, 115200, timeout = 1)
In the program of your Arduino:

    Serial.begin (115200);
>>>>>>> efm8-arduino-programmer/master
