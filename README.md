# Anet A8

Find here all sources I'm using for improving my Anet A8 3D printer and some other Anets.

Most of the files are not mine, you can check file headers for author references, I'll also try to refer all sources at the end of this file.

You are free to use all this files and documentation under your own risk.

# Anet A6

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

## References
- https://github.com/Lauszus/Sanguino
- https://github.com/MarlinFirmware/Marlin
- https://3dprint.wiki/reprap/firmware/anet/repetier/install
- https://github.com/repetier/Repetier-Firmware
