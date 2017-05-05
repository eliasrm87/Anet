# Anet A8

Find here all sources I'm using for improving my Anet A8 3D printer and some other Anets.

Most of the files are not mine, you can check file headers for author references, I'll also try to refer all sources at the end of this file.

**You are free to use/follow all this files and documentation at your own risk.**

# Anet A6 (Not working yet)

I only have an Anet A8, so everything I share here for that printer has been tested by my self on my own printer, I can not say the same for the A6, so be very careful when using what I have here on this printer.

## Arduino IDE hardware definition for Anet main board V1.0

### Arduino IDE setup
- Copy the Arduino folder content into your Arduino sketches folder
- Open arduino IDE
- Add the following url at "Additional Boards Manager URLs" on "preferences": https://raw.githubusercontent.com/Lauszus/Sanguino/master/package_lauszus_sanguino_index.json
- Install last version of "Arduino AVR Boards" and "Sanguino" using the boards manager

## Clearing EEPROM
Clearing EEPROM is very important if you are changing firmware family, for example from marlin based to repetier based.
If you are not sure, I recommend you to clear the EEPROM before flashing the new firmware.
For clearing the EEPROM follow the following steps:
- Open Arduino IDE
- Go to File -> Examples -> EEPROM -> eeprom_clear
- Select board "Anet V1.0"
- Click upload button
- Give, lets say, one minute for your printer to reset and execute the sketch

## Repetier firmware

### Build and upload repetier firmware
- Go to https://www.repetier.com/firmware/v092/
- Upload the configuration file from this repository
- Click on "Download" tab
- Click "Download complete firmware incl. these settings" button
- Open downloaded "repetier.ino" file with arduino IDE
- Select board "Anet V1.0"
- Click upload button

## Marlin firmware
*Work in progress*

## Burning bootloader

You may brick your main board if you do things like selecting a wrong board on the arduino IDE, forcing the system to flash a incorrect firmware or unplugging the USB while it is flashing. After that, you may not be able to flash your main board anymore and probably you will start getting errors like this:  

    avrdude: stk500_cmd(): programmer is out of sync

If this happens, first discard that you don't have a defective USB cable by replacing it. If you are still unable to flash your main board, most likely you are against a boot loader corruption, so your main board is probably "bricked". 

You can try to burn again the bootloader using an Arduino as ISP programer connected to your board following this [diagram](https://github.com/erm2587/Anet/blob/master/Pictures/ArduinoISP.gif) and following this steps:

- Plug the USB cable to the arduino board
- Open arduino IDE
- Open the ArduinoISP firmware (in Examples)
- Select the items in the Tools > Board and Tools > Serial Port menus that correspond to the arduino board you are using as the programmer (not the Anet main board being programmed)
- Upload the ArduinoISP sketch
- Dissconnect the USB cable from the arduino board
- Dissconnect everithing from your printer mainboard, even the power supply
- Wire your Arduino board to the board as shown in the [diagram](https://github.com/erm2587/Anet/blob/master/Pictures/ArduinoISP.gif)
- **Check your wirings at least three times, as a wrong wiring may destroy your Arduino and even your main board**
- Plug the USB cable to the arduino board
- Select the item "Anet V1.0" in the Tools > Board menu
- Select the Arduino as ISP in the Tools > Programmer menu
- Use the Burn Bootloader command
- If the burning finish without errors, disconnect all wires between the arduino and the main board and connect again everything to the main board (fans, motors, LCD, etc.)

Now you should be able to connect your USB cable to the main board, as usual, and flash any new firmware to it. I suggest you to start testing with the "Blink" example and check that the LED into the main board start to blink.

This steps has been taken from https://www.arduino.cc/en/Tutorial/ArduinoISP, consult it for extra information.

## References
- http://3dtoday.ru/upload/main/233/Anet.jpg
- https://github.com/Lauszus/Sanguino
- https://github.com/MarlinFirmware/Marlin
- https://3dprint.wiki/reprap/firmware/anet/repetier/install
- https://github.com/repetier/Repetier-Firmware
