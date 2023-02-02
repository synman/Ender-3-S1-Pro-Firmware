# Creality Ender-3 S1 Pro Firmware

<img width=400px src="https://user-images.githubusercontent.com/1299716/215980417-d70e84ea-0a16-4c25-bdba-8985cca5c6c9.png"/>

## USE AT YOUR OWN RISK ##

`Marlin 2.0.8` was built from the official <a href="https://github.com/CrealityOfficial/Ender-3S1/tree/s1_pro">Creality GitHub Repo</a> with fixes provided by <a href="https://github.com/Pethical">@Pethical</a>. 

`Marlin 2.1.2` was built from the official Marlin repository with all of the touchscreen handling Creality code ported/integrated into it.

`Marlin 2.1.x bugfix` is based on a periodic snapshot from the official Marlin repository's 2.1.x bugfix branch.  This should be considered bleeding edge and is bit more risky than the other two distributions, but has the added benefit of gaining access to new Marlin features before they are generally available.

Additionally, the following `Capabilities` and configuration items have been enabled / changed:

- Z Axis Microstepping set to .01 increments (still buggy)
- Extruder minimum temperature lowered to 170C
- Probing Margin reduced to 5mm
- Fast / Slow / Slow probing strategy
- Turn fans off when probing
- Preheat before probing (70C/70C)
- G26 Mesh Validation
- 5 x 5 Bilinear Mesh (25 points)
- G12 Clean the Nozzle
- Include ADC values when reporting temperature
- Emergency Parser
- Auto Report Position
- Report Fan Changes (not confirmed)
- Host Action Commands
- Host Prompt Support
- M486 Cancel Objects

There should be a noticable improvement in bed tramming accuracy, but likely minimal.  OctoPrint will light up with Action Command notifications and manage functions such as filament changes.  

## How to Install
Make sure you are running the latest version of the TouchPanel Display and the Machine before proceeding any further.  You can find the binaries and instructions here:  https://www.creality.com/pages/download-ender-3-s1-pro

### Identify your board
There are two different STM32 SoC chips used on the S1 Pro.  You can determine which one you have by looking at the Firmware Version within the display's About section.

- You have a `STM32F103RET6` if the F/W VER ends with `F1`
- You have a `STM32F401RC` if the F/W VER ends with `F4`

<img width="425" alt="Screenshot 2023-01-30 at 2 53 40 AM" src="https://user-images.githubusercontent.com/1299716/215419703-a4404966-8fa1-478c-ab97-1250666bcc03.png">

### Installation Plan
- Download the zip file from here that matches your board
- Unzip it and copy either the included .bin file or `STM32F4_UPDATE` directory to the root of an SD card
- Insert the SD card into your printer and power cycle it
- It shouldn't take more than 15-20 seconds for the process to complete
- Remove the SD card (delete the firmware file/s from it if you intend to use it with your printer)

## Restore Factory Settings
You must do a factory reset of your machine.  Issue the following commands to initialize your new firmware and clear out your prior 4x4 bed mesh:

- M502 ; Factory Restore
- M500 ; Save EEPROM
- M501 ; Load EEPROM

## Uninstall / Recovery
Reapply the official Creality firmware linked above.


## Source Code
https://github.com/synman/Ender-3S1/tree/firmware_troubleshooting
https://github.com/synman/Marlin/tree/2.1.2-ender-3-s1
https://github.com/synman/Marlin/tree/bugfix-2.1.x
