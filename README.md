# Creality Ender-3 S1 Pro and Plus Firmware

<img width=400px src="https://user-images.githubusercontent.com/1299716/215980417-d70e84ea-0a16-4c25-bdba-8985cca5c6c9.png"/>

## USE AT YOUR OWN RISK ##

`Marlin 2.0.8` was built from the official <a href="https://github.com/CrealityOfficial/Ender-3S1/tree/s1_pro">Creality GitHub Repo</a> with fixes provided by <a href="https://github.com/Pethical">@Pethical</a>. 

`2.1.2-ender-3-s1` was built from the official Marlin repository with all of the touchscreen handling Creality code ported/integrated into it.

`bugfix-2.1.x` is based on a periodic snapshot from the official Marlin repository's 2.1.x bugfix branch.  This should be considered bleeding edge and is bit more risky than the other two distributions, but has the added benefit of gaining access to new Marlin features before they are generally available.

Theoretically the base model S1 is supported as well assuming it has CR Touch probe and touchscreen installed.  The S1 Pro binaries should be able to be flashed to it.

Additionally, the following `Capabilities` and configuration items have been enabled / changed:

- Ender-3 S1 Pro and Plus supported
- Laser Module Enabled (unable to test)
- Bed Size set to 235mm x 225mm (S1 Pro)
- Unified Bed Leveling (UBL) or Bilinear Leveling (ABL)
- Probe X/Y offset updated to be more accurate
- Z Axis babystepping set to .01mm increments 
- Live Z Axis babystepping @ .01mm increments (sd print @ .05mm)
- M851 and M290 changes update Z-Offset on LCD
- Z-Offset UI updates notifies host
- Linear Advance is available (bugfix-2.1.x only)
- Input Shaping is availabe (bugfix-2.1.x only)
- Backlash Compensation and M425 supported (bugfix-2.1.x & 2.1.2 only)
- M73 Progress (bugfix-2.1.x & 2.1.2 only)
- M48 Probe Repeatability Test
- Extruder minimum temperature lowered to 170C
- Heatbreak fan extruder minimum temperature set to 80C
- Probing Margin reduced to 5mm (ABL)
- Fast / Slow / Slow probing strategy
- Turn fans off when probing (ABL)
- Preheat before probing (70C/70C) (ABL)
- G26 Mesh Validation
- 5 x 5 Bilinear Mesh (25 points) (ABL)
- 5 x 5 Unified Mesh (25 points) (_ubl25)
- 10 x 10 Unified Mesh (100 points) (_ubl100)
- G12 Clean the Nozzle
- Include ADC values when reporting temperature
- Emergency Parser
- Advanced Pause (M600 and M125)
- M117 Set LCD Message supported
- Auto Report Position
- Report Fan Changes for fans that support it
- Host Action Commands
- Host Prompt Support
- M486 Cancel Objects

* NOTE:  Laser functionality is untested.  You can help fix this by becoming a <a href="https://github.com/sponsors/synman">sponsor</a>!

There should be a noticable improvement in bed tramming accuracy, but likely minimal.  OctoPrint will light up with Action Command notifications and manage functions such as filament changes.  

## How to Install
### S1 Pro
Make sure you are running `v2.0.8.24` of the TouchPanel Display and the Machine before proceeding any further.  You can find the binaries and instructions here:  https://www.creality.com/pages/download-ender-3-s1-pro

<img width="600" alt="Screenshot 2023-02-04 at 12 04 52 PM" src="https://user-images.githubusercontent.com/1299716/216780180-3eb58264-e5ec-40b1-bfbc-97005d06daa1.png">

If for some reason you are unable to locate `Ender-3 S1_Pro_HWv24S1_301_SWV2.0.8.24F4_FDM_LASER` on the Creality site, you can find a mirror of it here: https://github.com/synman/Ender-3-S1-Pro-Firmware/tree/main/0_baseline_firmware

### S1 Plus
Make sure you are running `v2.0.8.25` of the TouchPanel Display and the Machine before proceeding any further.  You can find the binaries and instructions here:  https://www.creality.com/pages/download-ender-3-s1-plus

<img width="600" alt="Screenshot 2023-02-04 at 12 16 27 PM" src="https://user-images.githubusercontent.com/1299716/216780674-db231052-e95c-4d6d-9dac-e4eeae590e5e.png">

If for some reason you are unable to locate `Ender-3S1Plus_HWv24S1_301_SWV2.0.8.25F4_F401_FDM_LASER.zip` on the Creality site, you can find a mirror of it here: https://github.com/synman/Ender-3-S1-Pro-Firmware/tree/main/0_baseline_firmware

### Identify your board
There are two different STM32 SoC chips used on the S1 series machines.  You can determine which one you have by looking at the Firmware Version within the display's About section.

- You have a `STM32F103RET6` if the F/W VER ends with `F1`
- You have a `STM32F401RC` if the F/W VER ends with `F4`

<img width="425" alt="Screenshot 2023-01-30 at 2 53 40 AM" src="https://user-images.githubusercontent.com/1299716/215419703-a4404966-8fa1-478c-ab97-1250666bcc03.png">

### Installation Plan
- Download the zip file from here that matches your machine and board
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
#### 2.0.8 Stock Creality (merged into Marlin 2.0.8)
https://github.com/synman/Marlin/tree/2.0.8-ender-3-s1
#### 2.1.2 (Stable) Marlin
https://github.com/synman/Marlin/tree/2.1.2-ender-3-s1
#### 2.1.x (Bugfix) Marlin
https://github.com/synman/Marlin/tree/bugfix-2.1.x
