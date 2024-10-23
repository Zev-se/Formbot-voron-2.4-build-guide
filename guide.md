## Introduction

Formbot Voron 2.4 kits are generally a good value (high quality, inexpensive) but they include a bunch of Mods, so their build process differs from official Voron.  This divergence is poorly documented.  This document is our attempt to provide a detailed build guide for Formbot Voron 2.4 kits.

Please report any incorrect or missing info here on github or in the Voron or Formbot Discord.


## Types of kits

Formbot has sold a couple of different Voron 2.4 kits, and it's a bit unclear how they've changed.  We'll try to collect the info here, please update this document where it is incomplete or incorrect.

<details>
  <summary>"Voron 2.4 R2 Pro+ CoreXY 3D Printer Kit with M8P+CB1 Board and Canbus Wiring System" (ordered 2024-06-23)</summary>
  

Advertised features:
* TAP leveling sensor
* Filament runout sensor
* LED chamber illumination
* Nevermore air filter
* EBB SB2209 CAN (RP2020) (note errata here: <https://github.com/bigtreetech/EBB/issues/88#issuecomment-2120227957>)
* EBB SB0000 CAN
* 5" HDMI touch screen
* Stealthburner + CW2
* Manta M8P + CB1 motherboard
* Gates belts
* 440C linear guide rails
* Double-sided magnetic flexible PEI print sheet (textured on one side, smooth on the other)

Differences from mainline Voron 2.4:
* Bakelite spacers under the bed instead of M4 thumb nuts
* CAN toolhead board
* Umbilical toolhead wiring instead of cable chains

Noteworthy details:
* Uses standard microswitch XY endstops, not hall effect
* TAP uses OptoTap 2.4.1 optical sensor board <https://github.com/VoronDesign/Voron-Tap/tree/main/OptoTap>
* Comes with two PT1000 thermal sensors
* The heated bed has an NTC 100K B3950 thermistor.
* The "SB2209 CAN (RP2040)" includes ADXL345 accelerometer for input shaping

</details>

<details>
  <summary>"Voron 2.4 R2 Pro+ CoreXY 3D Printer Kit with M8P+CB1 Board and Canbus Wiring System" (ordered 2024-09-17, shipped from Czech warehouse)</summary>
  Main differences seem to be I got a M8P v2.0 board and only 1 PT1000 sensor.
  I've ordered a dragonburner HF, which came seperately. The kit comes standard with a V6 clone.
  This is the full BOM as advertised on the website at the time of buying:
  
![image](https://github.com/user-attachments/assets/fd71c404-1efa-4307-884f-6c9a8d4f4551)
![image](https://github.com/user-attachments/assets/393d47f7-c07c-46e9-b278-08e8bbacaffc)
![image](https://github.com/user-attachments/assets/6053423b-8034-40e9-8971-af1b120be359)


</details>

## The build process

A list of tools used to assemble the kit: [tools](tools.md)

These build instructions will reference the following manuals:
- [The Voron 2.4R2 Assembly Manual](https://github.com/VoronDesign/Voron-2/raw/Voron2.4/Manual/Assembly_Manual_2.4r2.pdf)
- [The Stealthburner Assembly Manual](https://github.com/VoronDesign/Voron-Stealthburner/raw/main/Manual/Assembly_Manual_SB.pdf)
- [The Voron Tap Assembly Manual](https://github.com/VoronDesign/Voron-Tap/blob/main/Manual/Assembly_Manual_Tap.pdf)
- [Voron Tap r8 errata](https://github.com/VoronDesign/Voron-Tap/blob/main/Manual/R8_errata.md)
- [The Formbot wiring guide](https://github.com/FORMBOT/Voron-2.4/tree/main/Diagrams) ([old version](https://drive.google.com/file/d/19wdkwaP-MP6JrulkZ-r0Kav1kbvxzPzk/view?usp=sharing)) and [schematic overview](https://drive.google.com/file/d/150u_T2eWLyC1sthwrm-xLMOyLApJ4kwb/view)
- [Pinout diagram for your controller](https://docs.vorondesign.com/build/electrical/controller_wiring.html#voron-2), [M8P V1.0](https://github.com/bigtreetech/Manta-M8P/blob/master/V1.0_V1.1/Hardware/BIGTREETECH%20MANTA%20M8P%20V1.0%20PinOut.png) and [M8P V2.0](https://github.com/bigtreetech/Manta-M8P/blob/master/V2.0/Hardware/BIGTREETECH%20MANTA%20M8P%20V2.0%20PinOut.png)
- [Pinout diagram of the SB2209 toolhead PCB](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2209%20CAN%20(RP2040)/Hardware/EBB%20SB2209%20CAN%20V1.0%EF%BC%88RP2040%EF%BC%89-Pin.png)
- [Bigtreetech EBB SB2209 CAN (RP2040) manual](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2209%20CAN%20(RP2040)/Build%20Guide/EBB%20SB2209%20CAN%20V1.0%EF%BC%88RP2040%EF%BC%89Build%20Guide_20240626.pdf)
- [Bigtreetech MANTA M8P V1.0&V1.1 User Manual](https://github.com/bigtreetech/Manta-M8P/blob/master/V1.0_V1.1/BIGTREETECH%20MANTA%20M8P%20V1.0%26V1.1%20User%20Manual.pdf) or [Bigtreetech MANTA M8P V2 User Manual](https://github.com/bigtreetech/Manta-M8P/blob/master/V2.0/BIGTREETECH%20MANTA%20M8P%20V2.0%20User%20Manual.pdf)
- [Esoterical CAN Bus Guide](https://canbus.esoterical.online/)

Build sequence:

| Manual               | Pages   | Comment
|----------------------|---------|---
| Voron 2.4R2          | 1-14    | Smooth sailing.
| Voron 2.4R2          | 15      | [These extrusion jigs](https://mods.vorondesign.com/details/SSoHrEC3VElDLwDLw2GA5Q) can be useful to ensure the frame is built square.
| Voron 2.4R2          | 16-27   | Smooth sailing.
|                      | 28      | Be sure to remove all protective paper or plastic film from both sides of the Deck Panel before mounting.  When mounted, the upper face of the Deck Panel will be visible inside the printer, and the lower face will be hidden inside the electronics bay under the printer.  So select whichever face you want to see all the time to face upwards.
|                      | 29      | On 250, mount the DIN rails as shown in the Voron 2.4R2 Manual (you may have to shorten them slightly to fit).  On 300 (and 350?) turn the DIN rails 90 degrees and mount them parallel with the Bed Extrusions.
|                      | 30-38   |
|                      | 39      | If you build a 300x300 Formbot turn one of the motors 90 degrees so that the cable is on the same side as the two screws of the bracket, this will be Z1 later
|                      | 40-53   |
|                      | 54      | After carefully installing the flexplate magnet onto the aluminum bed plate, you need to cut away part of the magnet to expose the four bed plate mounting holes.  Note that you do *not* need to cut away the magnet over the two threaded holes near the rear edge of the plate, because these will be accessed from below, not from above.  Locate the bed plate mounting holes by drilling through the magnet from below, using the four existing holes as guides, then cut the magnet using a sharp knife.  ![](/images/flexplate-magnet-holes.jpg)
|                      | 55-57   |
|                      | 58      | The Formbot kit comes with "Bakelite Isolation Columns", use these instead of M4 nuts as spacers.  ![](/images/bakelite-isolation-columns.png)
|                      | 59-63   |
|                      | 64      | I'm using the default Voron Design `a_drive_frame_upper` part, not Formbot's version.  I'm then using @decidophobia's "Voron V2.4 PG7 Umbilical & Y Endstop Relocation with cable cutout - REMIX" part from printables to mount the Y endstop and anchor the PG7 gland.  <https://www.printables.com/model/527499-voron-v24-pg7-umbilical-y-endstop-relocation-with->
|                      | 65-83   |
|                      | 84      | Do not install heat-set threaded inserts into the cable chain mount, the Formbot kit uses an umbilical instead of cable chains.
|                      | 85-103  |
|                      | 104     | Do not install the cable chain mount, use M5x10 BHCS to attach both XY Joints to the gantry.
|                      | 105-109 |
|                      | 110     | Use the part for normal microswitch endstops (`z_joint_upper`), not the Hall effect version.
|                      | 111-113 |
|                      | 114     | There are a couple of options to make hanging the gantry easier: [@Nero3D's trick](https://www.youtube.com/watch?v=YEl5FNvi8Bs&t=10489s), or [Voron Z-Locks](https://github.com/VoronDesign/VoronUsers/tree/main/printer_mods/tallman5/z-locks), or [@andimoto's "Voron v2.4 Gantry Installation Hooks"](https://www.printables.com/model/173635-voron-v24-gantry-installation-hook-new-version)
|                      | 115-125 |
|                      | 126-127 | Route the A and B belts at this point and leave them loose in front of the X rail.
|                      | 128     |
|                      | 129-131 | Skip these pages, TAP replaces the X carriage.
| Voron TAP            | 1-17    |
| Voron TAP            | 18      | Use the Voron project's printed [MGN9 Assembly Tool](https://github.com/VoronDesign/Voron-Tap/blob/main/STLs/MGN9_Assembly_Tool.stl) rather than the similar part that comes with Formbot's kit.  Formbot's part is too fat and causes some inconvenience when reinstalling the carriage onto the rail later.
| Voron TAP            | 19-23   |
| Voron TAP            | 24      | Per the errata (you did read the errata, right) the threaded inserts are installed slightly differently.
| Voron TAP            | 25-26   |
| Voron TAP            | 27      | Per the errata, the two M3x6 FHCS that thread in to the Tap\_Front part at an angle may be replaced with magnets, e.g. if your screws are non-magnetic. ![](/images/Tap_Front.png) ![](/images/tap-magnet-option.png)
| Voron TAP            | 28      |
| Voron TAP            | 29      | Per the errata we use M3x6, M3x12, and M3x16 SHCS to attach the rail.
| Voron TAP            | 30      | The 2024-06-23 kit uses a "Trident style" X-axis microswitch.
| Voron TAP            | 31      | Attach the belts to the Center and attach the Center to the MGN12 linear rail of the X axis.  This video is helpful: <https://www.youtube.com/watch?v=mJNCn72lQpU>
| Voron 2.4R2          | 132-138 | Route the belts.
| Voron 2.4R2          | 139-141 | Skip these, use the Tap instead.
| Voron 2.4R2          | 142     | Check your work.
| Voron TAP            | 32      | If there is not sufficient clearance to install the MGN9H carriage onto its rail from the top, temporarily remove the lowest rail screw (the carriage stop, with the heat-set insert spacer) and install the carriage from the bottom, then reinstall the carriage stop screw. ![](/images/tap-carriage-install-0.jpg) ![](/images/tap-carriage-install-1.jpg)
| Voron TAP            | 33      | I had to avoid tucking the belts through the slots in the Front part, it interfered with the motion of the Tap.
| Voron TAP            | 34      |
| Stealthburner        | 1-10    |
| Stealthburner        | 11      | If you have a CAN kit using EBB SB2209/SB0000, use the Bigtreetech part: <https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/STL/Main_Body_EBB.stl>
| Stealthburner        | 12      |
| Stealthburner        | 13      | The 2024-06-23 kit uses a toolhead PCB (EBB SB2209 RP2040), so install the two threaded inserts for the optional toolhead PCB.
| Stealthburner        | 14      | For the 2024-06-23 kit: uses umbilical instead of cable chains so skip this page.
| Stealthburner        | 15-16   |
| Stealthburner        | 17      | For the 2024-06-23 kit: BMG idler assembly may consist of three parts like the manual shows, or it may consists of just two parts.  As long as the axle snaps tightly in to the guidler and the gear spins freely and without wobble it's probably ok.  If you have problems with the axle popping loose from the guidler, carefully place a drop of cyanoacrylate adhesive (Super glue) in the two places where the axle snaps into the guidler.  Be careful not to glue the gear to the axle! ![](/images/BMG-Idler-Assembly-manual.png) ![](/images/BMG-Idler-Assembly-actual.jpg)
| Stealthburner        | 18-20   |
| Stealthburner        | 21      | The Drive Assembly may come as a single piece, with no assembly needed.  ![](/images/single-part-Drive-Assembly.jpg)
| Stealthburner        | 22-30   |
| Stealthburner        | 31-32   | For kits with umbilical, skip this part and these pages.  Later we'll attach the BTT "Cable Bridge" that replaces the stock Voron "Chain Anchor".
| Stealthburner        | 33      |
| Stealthburner        | 34      | If you have a CAN kit using EBB SB2209/SB000, use the Bigtreetech part: <https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/STL/Cable_Cover_For_PCB_V1.1.STL>
| Stealthburner        | 35-39   |
| Stealthburner        | 40      | Mind the orientation of the hotend. With dragonburner hotends the heat block needs to point forward or it will touch and probably melt the TAP plate (see [this](https://youtu.be/7x-eafpESLc?t=1027) video).
| Stealthburner        | 41-42   |
| Stealthburner        | 43      | Some kits will come with multiple PTFE tubes, use the shorter one with ~4 mm OD and ~2 mm ID.
| Stealthburner        | 44-54   |
| Stealthburner        | 55      | Discard the half of the fan housing that doesn't have the fan motor and rotor mounted on it.
| Stealthburner        | 56      | Don't screw in the screws yet, they'll come as part of the SB2209.
| EBB SB2209           | N/A     | To work around [this problem](https://github.com/bigtreetech/EBB/issues/88), solder a 10 kOhm resistor between GPIO21 and +5V on the Probe connector. ![](/images/SB2209-RP2040-pullup.jpg)
| EBB SB2209           | 2       | Install the SB0000 on top of the fan, then screw in the screws.
| EBB SB2209           | 3-4     | Set the SB2209 jumper for the voltage shown on your fans, mine were all 24V. Make sure you use the correct sized jumpers, there are several in the kit and they need to fit snugly to make a solid connection.
| EBB SB2209           | 5       | Skip this page if your fans have 2-wire connections (non-PWM fans).
| EBB SB2209           | 6-9     |
| EBB SB2209           | 10      | Install the jumper for the 120R terminating resistor.
| EBB SB2209           | 11      |
| Stealthburner        | 57-58   |
| Stealthburner        | 59-65   | Skip, not used with Tap.
| Stealthburner        | 66      | The Printhead assembly mates flush against the Tap assembly, and is initially held by the two M3x16 SHCS screws from Tap page 25 and resting on the two M3x6 BHCS from Tap page 27.
| Stealthburner        | 67      | Don't do this page, we did it as part of the EBB manual.
| Stealthburner        | 68-69   | Don't do these pages, there's an ADXL345 on the SB2209 (RP2040).
| Voron TAP            | 35      | Verify Printhead alignment.  If needed, modify rear of printhead with a file or dremel.  Tighten the two upper screws to hold the printhead in place.
| EBB SB2209           | 12-14   |
| EBB SB2209           | 15      | Skip this page, the kit does not use a Prox Z endstop/probe.
| EBB SB2209           | 16      |
| EBB SB2209           | 17      | The kit comes with a pre-crimped probe cable to use for Tap and the Filament Runout Sensor.
| EBB SB2209           | 18      | Skip this page, the kit does not use BLTouch or Klicky probe.
| EBB SB2209           | 19      | Final assembly of Stealthburner!
| EBB SB2209           | 20-24   | There is a PG7 Cable gland in the kit and [printed part](https://github.com/FORMBOT/Voron-2.4/blob/main/STL/Accent/PG7-Umbilical%20Motor%20Mount.stl) to wire the CAN cable (with piano wire) to the A drive. Unscrew the PG7 connector, route the CAN wire through (you might need to remove the rubber insert first to get the 2 pin connector through), then screw in the bottom into the printed part and screw the top into the bottom part, this acts as cable relief so the cable should have been captured snugly. Make sure you move the gantry around so the CAN cable is long enough to allow full range of movement.
| EBB M8P              | 16 (V1) or 12 (V2) | In order to flash the toolhead you need the CB1. Install the CB1 board onto the M8P. Make sure the board is seated correctly on both sides, there should be an audible click as the connectors snap in place.
| EBB M8P              | 24-35 (V1) or 20-31 (V2) | Follow the instructions to flash an SD card with a compatible image. The M8P board has 2 SD card slots, one for the M8P firmware, another for the SoC. Make sure you put the SD card in the SoC SD card slot. You can power the M8P and CB1 from USB if you set the USB 5V jumper (make sure to remove this jumper once you switch to 24V power). Once you have an ssh connection you can continue
| EBB SB2209           | 25-29   | Flash the EBB SB2240.  I had to unplug USB, press and hold BOOT, and reconnect USB in order to get it into bootloader mode, clicking the RST button did not work. This requires you to have the main SoC running (CB1, CM4, Raspberry PI, ..)
| Voron TAP            | 36      |
| Voron 2.4R2          | 143-144 | Skip these pages, the kit doesn't use a Z probe (uses Tap instead).
| Voron 2.4R2          | 145     | Skip this pages, the kit doesn't use a hall-effect X endstop.
| Voron 2.4R2          | 146-149 |
| Voron 2.4R2          | 150-152 | Skip these pages, the kit does not use a Raspberry Pi or a 5V power supply.
| Voron 2.4R2          | 153     | Put the mounts on the 24V power supply.
| Voron 2.4R2          | 154-155 | Put the mounts on the Manta M8P using the parts from the bigtreetech/Manta-M8P repo, using 4x M3-6 BHCS.
| Voron 2.4R2          | 156     | Dont forget to change the fuse, it's shipped with a 10A fuse. It should be changed for a 4A for 230V and 8A for 110V
| Voron 2.4R2          | 157     |
| Voron 2.4R2          | 158-161 | Skip these pages, the kit uses Tap instead of a Z endstop.
| Voron 2.4R2          | 162-164 | Different versions of this kit handle X & Y endstops (limit switches) in different ways. Newer versions of the kit use SB2209 to put the X endstop on the toolhead and the Y endstop on the right-rear coreXY motor: <https://www.printables.com/model/527499-voron-v24-pg7-umbilical-y-endstop-relocation-with->. The older version of the kit mounts the limit switches in a different way than mainline Voron: ![](/images/voron_limit_switch.png) ![](/images/wrongly_mounted_switch.jpeg)
| Voron 2.4R2          | 165-167 |
| Voron 2.4R2          | 168     | Note: For the rest of the assembly process, refer to the Voron 2.4r2 manual and the Formbot wiring guide for placement of the electronics.
| Voron 2.4R2          | 169     | Install the 24V power supply and its mounts on the DIN rail.  For 300mm, mount as shown in the Formbot Wiring Guide.  For 250mm, mount as shown in the Voron 2.4r2 manual. Make sure you add the extra mounting bracket.
| Voron 2.4R2          | 170     | Install the Manta 8P controller and its mounts on the DIN rail.
| Voron 2.4R2          | 171     |
| Voron 2.4R2          | 172     | Skip this page, no 5V supply with this kit.
| Voron 2.4R2          | 173     |
| Voron 2.4R2          | 174-179 | Skip these pages, the Formbot kit uses a Manta M8P control board instead.  Follow the instructions here instead: <https://docs.vorondesign.com/build/electrical/v2_m8p_wiring.html>. My kit came with BTT TMC2209 V1.3 stepper motor drivers, verify yours are too, otherwise the jumpers in the linked document might need to be set differently.
| Formbot Wiring guide |         | For older (non-CAN) kits: Mount the components as shown on the image, note that is the 350x350 so if you build a smaller printer it will be tighter. There's a picture further down in this guide with what is what. 
| Formbot Wiring guide |         | The CAN cable has 2 leads for 24V power, you need to crimp these and connect them to the PSU (I used a bit of wire to extend them so I didn't have to unravel the CAN communication wires)
| Formbot Wiring guide |         | If you can't find the 3 IN 6 OUT terminals in your kit, check the bag with the exhaust parts, in my case it was tucked away in there
| Formbot Wiring guide |         | If your frame is anodized the coating will not be conductive, when attaching protective earth to the frame, scrape away some coating so the T-nut makes a solid contact. You can test for continuity on any frame screw on all the extrusions to ensure the frame is properly earthed.
| Voron 2.4R2          | 180-183 | Wire up the 24V PSU.  Test it before connecting 24V to anything.
| Voron 2.4R2          | 184-185 |
| Voron 2.4R2          | 186-189 | Skip these pages, the kit does not include Wago clamps.
| Voron 2.4R2          | 190-191 | Skip these pages, the kit does not include a 5V PSU or a Raspberry Pi.
| Voron 2.4R2          | 192     | This kit does not include an Octopus control board.  Follow the instructions here instead: <https://docs.vorondesign.com/build/electrical/v2_m8p_wiring.html>
| EBB M8P              |         | Make sure to install the 120ohm termination resistor on the M8P as well, the M8P is the start of the CAN bus and the SB2209 is the end, hence why both need to have termination. 
| Esoterical CAN Guide |         | At this point everything is set up to run from 24V (make sure you have removed the USB 5V jumpers or you will fry the USB controller), including the CAN cable power. Plug in the CAN connector on the toolhead, and the connector on the M8P.
| Esoterical CAN Guide |         | Make the M8P a USB-CAN bridge. There is no dedicated CAN board so the M8P will act as a bridge between the internal USB communication with the CB1 and the CAN bus with M8P and SB2209 as CAN devices
| Esoterical CAN Guide |         | Follow the Mainboard flashing instructions. The M8P V1 and V2 have different settings (different chip, different offset, different crystal), make sure to check the correct EBB M8P guide. For example the CAN pins on the M8P V2 are PD0/PD1 ([pinout](https://github.com/bigtreetech/Manta-M8P/blob/master/V2.0/Hardware/BIGTREETECH%20MANTA%20M8P%20V2.0%20PinOut.png) but check the pinout diagram of your board)
| Esoterical CAN Guide |         | Follow the Toolhead flashing instructions. If you've already flashed katapult in a previous step with the correct CAN settings it should show up on the CAN bus, you can then flash klipper over CAN0. If not follow the instructions meticiulously
| Voron 2.4R2          | 193     | Run the Z motor wires, but note that this kit does not include an Octopus control board.  Follow the instructions here instead: <https://docs.vorondesign.com/build/electrical/v2_m8p_wiring.html>
| Voron 2.4R2          | 194-199 | Older non-CAN, non-umbilical kit: mount cables in chains before mounting chains as it will be hard to do otherwise. Also don't forget the extra LED cable.  Newer kit with CAN & umbilical: skip these pages, the umbilical replaces the X and Y cable chains.
| Voron 2.4R2          | 200     | The B-motor cable is routed in the 2020 grove under the gantry and held in place with a plastic cover instead of zipties.  Trim the plastic cover to length.  ![](/images/A_B_motor_cable.jpeg)
| Voron 2.4R2          | 201-202 | Mount the two ends without the chain attached.  Adjust the number of links in the Z cable chain to get it to the correct length.  Open the gates/covers in the chain links before mounting. Temporarily remove the PG7 bracket from the B motor mount to be able to attach the Z chain.
| Voron 2.4R2          | 203     |
| Voron 2.4R2          | 204     | Skip this page if you have a newer kit with CAN/umbilical, it has no cables routed along the gantry.
| Voron 2.4R2          | 205-209 | Skip these pages, follow the M8P instructions on the Voron Designs website instead: <https://docs.vorondesign.com/build/electrical/v2_m8p_wiring.html>.  Do the Electrical Wiring, Software Installation sections.
| Software config      |         | Follow the Software Configuration section loosely. Additional things need to be set up such as the SB2209 and can uuids instead of serial
| Software config      |         | Follow the Esoterical CAN Guide final steps to configure both [mcu] with canbus uuids so Klipper will recognize them. Note that when Klipper ingests the MCU they won't be visible through the can_query command to list them anymore.
| Software config      |         | Configure the SB2209 Toolhead, starting from the sample cfg provided [here](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2209%20CAN%20(RP2040)/sample-bigtreetech-ebb-sb-rp2040-canbus-v1.0.cfg). Make use of the pinout diagram to verify that the GPIO's used are correct with how you plugged things in. If you have a PT1000 temperature sensor plugged in into the 4 pin 31865 socket, remove the sensor_pin and sensor_type in extruder and uncomment the sensor_type: MAX31865 block. The temperature is accessed through communication with the MAX31865 chip
| Software config      |         | Configure the M8P mainboard, start from the provided sample cfg on the Voron repo [here](https://github.com/VoronDesign/Voron-2/tree/Voron2.4/firmware/klipper_configurations/M8P). Remove unnecessary things, verify the pins with the pinout diagram, the heater bed sensor type you can find on the back of the heater, mine was Generic 3950. Don't forget to set the X-endstop to the toolhead GPIO pin (when referencing a GPIO pin from a different MCU, you need to prefix it with its name so it becomes `pin: EBBCAN:gpio6`). Don't forget to copy over the extruder settings to the toolhead config, the sample SB2209 config is not set up for Clockwork 2.
| Software config      |         | Configure TAP, follow the post-install instructions on the [github page](https://github.com/VoronDesign/Voron-Tap). You will need to pull up the pin with `^`, with the provided wiring TAP is connected to gpio22 so it becomes `pin: ^EBBCan:gpio22` (verify with your pinout if it's the same for you). Skip PROBE_CALIBRATE for now, do that after homing and quad gantry levelling when the Initial Startup section on the Voron website calls for it.
|                      |         | Continue on the Voron website with the Initial startup, Slicer Setup, and First Print sections. First print wooo!
| Voron 2.4R2          | 210     |
| Voron 2.4R2          | 211     | Skip this page, the Formbot kit uses a different display with different mounting parts.
| Voron 2.4R2          | 212-213 |
| Voron 2.4R2          | 214-216 | Skip this page, the Formbot kit uses a different display with different mounting parts.
| Voron 2.4R2          | 217-219 |
| Voron 2.4R2          | 220-221 | Skip these pages, mount & hook up the 5" HDMI screen instead.
| Voron 2.4R2          | 222-230 |
| Voron 2.4R2          | 231     | Note the wiring of the fans will depend on your controller board, on my Manta M8P I used `FAN0` and `FAN1` at 24V, see <https://github.com/bigtreetech/Manta-M8P/blob/master/V1.0_V1.1/Hardware/BIGTREETECH%20MANTA%20M8P%20V1.1%20PinOut.png>
| Voron 2.4R2          | 232     | Use the red VFB tape, not the yellow foam tape.
| Voron 2.4R2          | 233-234 |
| Voron 2.4R2          | 235-236 | I found it easier to start with the screws and hammer head T-nuts off the Z belt covers.  I slid the Z belt cover into place, inserted the hammer head T-nut into the extrusion slot, slid it under the hole in the Z belt cover, and screwed in the screw.
| Voron 2.4R2          | 237-244 | Hammer head T-nuts are not my favorite, super fiddly. What seemed to work for me was to put the hammernuts on the screws a couple of turns, then hold the part in place with the hammernuts inserted in the channel, then *loosen* the screw so the hammernut completely backs out against the back of the extrusion channel, and then tighten. Loosening it first ensures it's completely in the extrusion channel and can turn while tightening. Once I did it like that installing the panels were a breeze.
| Voron 2.4R2          | 245-247 |
| Voron 2.4R2          | 248-249 | Attach the hinges to the doors but don't attach the handles.  Test fit the doors and sand the edges to fit, then attach the handles.
| Voron 2.4R2          | 250-251 |
| Voron 2.4R2          | 252     | The Formbot kit supplies the filter access cover, but feel free to ignore that part and print your own if you want it in the accent color.
| Voron 2.4R2          | 253-259 |

Voron V2.4R2 & Formbot Wiring PDF: Attach cables between breakout board and control board. When you have attached the last few cables you are mostly done with what you can do now, don't forgett to download and install the [Big tree tech PI version](https://github.com/bigtreetech/BTT-Pi) and from it flash the octopus board via the other smaller included SD-card.

[Software Configuration](https://docs.vorondesign.com/build/software/configuration.html)

Now follow the post build instructions to make sure you've done everything correct

For tuning I've found that the Voron website is a bit sparse, Bed meshing section is okay (note that Klipper supports Adaptive bed meshing now). For input shaping and belt tension similarity testing I recommend [Klippain](https://github.com/Frix-x/klippain) and general tuning [Ellis print tuning guide](https://ellis3dp.com/Print-Tuning-Guide/articles/index_tuning.html).

## Notes from the build

### The printed parts kit from Formbot
- As my old printer had acted up I decided to buy a kit of parts from Formbot (instead of using the print it forward program). This kit was mostly fine but there are three templates used when mounting the rails on the extrusion. I'm guessing most people who buy this kit of printed parts don't have a working printer at the moment. It would be nice if these were included. I guess some would have a printer that could print these in PLA but still. It's three very small parts to include I would happily pay an extra few bucks for. They are avalible in in the Voron STL's as **MGN12_rail_guide_x2.stl**, **MGN9_rail_guide_x2.stl** and **pulley_jig.stl**.

- A quick note about that [kit](https://www.formbot3d.com/products/high-quality-3d-printed-parts-for-voron-24-pro-kit?VariantsId=11047), it also would be nice if they linked what filament they used so that one could print new matching parts when done.

- One of these printed parts was I bit to tight. The part holds the gantry together. One of the A-B belt weels got too pinched. This happens, the tolarances are very fine. I shimed the part with two layers of craft paper and it now works perfectly.

- The bracket for the cables between the smaller cable chains shown on page 204 of the Voron 2.4R2 PDF was a bit to tight (see image above), I used a drillbit and just removed some plastic by hand. It's also hard to cram all cables and a cable sleeve into, if I did not plan on modding the printer with a canbus I would probalby redesign this.

- The Voron Tap plate is different from the Voron documentation, this is the R8 version. See differances in image below.
![](/images/SB_mount.jpg)
Original tap design:
![](/images/SB_original_mount.png)

- The tap plate also did not have the cone guiding you to the correct depth of the heatset incerts. Not sure why this has been changed.
![](/images/tap_unclear_depth_heatset_incerts.jpeg)
How the original STL looks:
![](/images/tap_cone.png)


- The arm to cables mounted on the back of the Clockwork 2 is the wrong color. Not a big deal, just be aware when looking for it.

- Bending the mounts with a screwdriver helped with negitioating them to bend the way they need to.
![](/images/stiff_mount_tip.jpeg)

### Notes

For anyone new here's a breakdown of what is what.
![](/images/what_is_what.png)

RED - Motor turned 90 degrees (Formbot 300X300 kit)

PINK - This is the on off switch for the heated bed, it's not an invertor as one might think. In the Voron documentation this is called the AC BED CONTROL. To be specific this is a Solid State Relay (SSR). 

YELLOW - PSU, the powersupply. In the Voron documentation this is called the LRS-200-24 PSU.

GREEN - RASPBERRY PI.

DARK BLUE - Controller. This board controlles the motors and is basically a break out board. Before Klipper this board used to run on Marlin and there was no PI. It's a bit confusing. Just know this is refered to as the CONTROLLER BOARD in the Voron documentation.

LIGHT BLUE - Break out board (this is replaced with canbus is later kits)

ORANGE - This is Formbots own PCB, in the Voron documentation this is the same as using the WAGO clamps.

- The plastic bracket included in the kit which is for a SBB EBB board isn't needed. Just skip this.
![](/images/not_needed_bracket.jpeg)

- To mount the SBB EBB break out board i used M3x6 screws from the kit.

- The Bearings on page 17 of the Stealthburner PDF are different from the ones in the kit. Not a problem, just be aware.
![](/images/other_bearings.jpeg)

- There's no z endstop included because of TAP, there's also no 5V PSU included because the BTT PI runs on 24V. Not a problem, just be aware so you don't spend time searching for items that simply aren't there.

- Don't forget to change the fuse. It might be hard to know where to find it. Here's an image. 4A for 230V and 8A for 110V. Here's the nice explaination I got "The Bed has 650 Watt + PSU 200 Watt...  850 Watt / 230V = 3,7 Amp".
![](/images/fuse.jpeg)

- I found it to be unclear how many of what panel mounts are needed. But the STLs actually says that I noticed later. For instance bottom_panel_clip_x4.stl, the x4 is the amout needed. I printed these in PLA for now. I need the panels to print ABS so it's a bit of a catch 22.

- The cable chains are a bit too long, you can remove links so this really isn't an issue. Rather nice having a few extra. A tip is to mount the ends separatly and connect them once all the cables are inside (as the snaps closing the chain will face down towards the 20x20 extrusion).
![](/images/Cable_chain_too_long.jpeg)
![](/images/cable_chain_tip.jpeg)

- From what I remember, the kit said to include a nevermore filter. It dosen't. It does include some hardware, fans, coal, WAGO-clips, a cable, some screws. But it does not include the plastic parts. This is a bit of an issue. I would want the filter to print ABS, but to do so I need to print the filter, in ABS. I opted to first print all panel clips in PLA and then print the nevermore parts with a window open. The printer isn't tuned properly but I also don't want to do that without the filter. So this is good enough for now. When the printer is tuned I will reprint this. 

- I can also say mounting this was hell, getting the heated bed back in place took some time. As you can see I choose to print the [V6 version](https://github.com/nevermore3d/Nevermore_Micro/tree/master/V6) and not the [Formbot version](https://drive.google.com/file/d/13Aie-BDK4WHfmduJOtDo85zog0QI33kh/view) (if link is broken, they can be found [here](https://drive.google.com/file/d/13Aie-BDK4WHfmduJOtDo85zog0QI33kh/view)). I didn't have a JST connector over so I've temporarily used other connectors.
![](/images/never_more_temp_connectors.jpeg)

- As you can see the non tuned printer has a bit of work ahead before it prints well.
![](/images/untuned_printer_0.jpeg)
![](/images/untuned_printer_1.jpeg)

- As there were more 1mm foam-tape included I also added it to the inside of the doors which made a real impact.

- When installing the Fly-ADXL345-USB (Mellow Fly used for imput shaping) I had some issues, first with getting the board into BOOTSEL mode and late when flashing. The first issue I have no idea of how it happened. I did the same thing about 50 times and all of a sudden it worked. The second issue was a typo from my side, please don't forget `/dev/serial/by-id/` in this command 
```bash
make KCONFIG_CONFIG=config.adxl345 flash FLASH_DEVICE=/dev/serial/by-id/usb-katapult_rp2040_E662549553812C2B-if00
```

## Summary
All in all it's been a fun build. It now prints parts and seems happy. It took some time getting the config correct with all pins. I also mounted some led strips at the top of the chamber. I was a bit affraid of crashing the whole printer badly but thanks to the well written [initial setup guide](https://docs.vorondesign.com/build/startup/) everything work out fine. Just remember TAP will figure out where true Z is. Make sure to put you `z_offset` to what it should be. I used TBD and that seems to work okay. Also remember there is a huge community, I asked for help several times when I needed it. Just be mindful it's a community and not a support. I'm really happy I toke this project on and built what seems like a printer that will be my new working horse. Looking forward on tweeking it and improving print quality, one commit at a time.

If you're interested in my config files they are available [here](https://github.com/Zev-se/voron_2.4_config).
