## Introduction

Formbot Voron 2.4 kits are generally a good value (high quality, inexpensive) but they include a bunch of Mods, so their build process differs from official Voron.  This divergence is poorly documented.  This document is our attempt to provide a detailed build guide for Formbot Voron 2.4 kits.

Please report any incorrect or missing info here on github or in the Voron or Formbot Discord.


## Types of kits

Formbot has sold a couple of different Voron 2.4 kits, and it's a bit unclear how they've changed.  We'll try to collect the info here, please update this document where it is incomplete or incorrect.


### "Voron 2.4 R2 Pro+ CoreXY 3D Printer Kit with M8P+CB1 Board and Canbus Wiring System" (ordered 2024-06-23)

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

Differences from mainline Voron 2.4:
* Bakelite spacers under the bed instead of M4 thumb nuts
* CAN toolhead board
* Umbilical toolhead wiring instead of cable chains

Noteworthy details:
* Uses standard microswitch XY endstops, not hall effect
* TAP uses OptoTap 2.4.1 optical sensor board <https://github.com/VoronDesign/Voron-Tap/tree/main/OptoTap>
* Comes with two PT1000 thermal sensors
* The "SB2209 CAN (RP2040)" includes ADXL345 accelerometer for input shaping


## The build process

A list of tools used to assemble the kit: [tools](tools.md)

These build instructions will reference the following manuals:
- [The Voron 2.4R2 Assembly Manual](https://github.com/VoronDesign/Voron-2/raw/Voron2.4/Manual/Assembly_Manual_2.4r2.pdf)
- [The Stealthburner Assembly Manual](https://github.com/VoronDesign/Voron-Stealthburner/raw/main/Manual/Assembly_Manual_SB.pdf)
- [The Voron Tap Assembly Manual](https://github.com/VoronDesign/Voron-Tap/blob/main/Manual/Assembly_Manual_Tap.pdf)
- [Voron Tap r8 errata](https://github.com/VoronDesign/Voron-Tap/blob/main/Manual/R8_errata.md)
- [The Formbot wiring guide](https://drive.google.com/file/d/19wdkwaP-MP6JrulkZ-r0Kav1kbvxzPzk/view?usp=sharing)
- [Pinout diagram for your controller](https://docs.vorondesign.com/build/electrical/controller_wiring.html#voron-2)
- [Bigtreetech EBB SB2209 CAN (RP2040) manual](https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2209%20CAN%20(RP2040)/Build%20Guide/EBB%20SB2209%20CAN%20V1.0%EF%BC%88RP2040%EF%BC%89Build%20Guide_20240626.pdf)
- [Bigtreetech MANTA M8P V1.0&V1.1 User Manual](https://github.com/bigtreetech/Manta-M8P/blob/master/V1.0_V1.1/BIGTREETECH%20MANTA%20M8P%20V1.0%26V1.1%20User%20Manual.pdf)

Build sequence:

| Manual               | Pages   | Comment
|----------------------|---------|---
| Voron 2.4R2          | 1-27    | Smooth sailing.
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
|                      | 114     | Consider using @Nero3D's trick to hang the gantry <https://www.youtube.com/watch?v=YEl5FNvi8Bs&t=10489s>, or using @andimoto's "Voron v2.4 Gantry Installation Hooks" <https://www.printables.com/model/173635-voron-v24-gantry-installation-hook-new-version>
|                      | 115-125 |
|                      | 126-127 | Route the A and B belts at this point and leave them loose in front of the X rail.
|                      | 128     |
|                      | 129-l31 | Skip these pages, TAP replaces the X carriage.
| Voron TAP            | 1-23    |
| Voron TAP            | 24      | Per the errata (you did read the errata, right) the threaded inserts are installed slightly differently.
| Voron TAP            | 25-28   |
| Voron TAP            | 29      | Per the errata we use M3x6, M3x12, and M3x16 SHCS to attach the rail.
| Voron TAP            | 30      | The 2024-06-23 kit uses a "Trident style" X-axis microswitch.
| Voron TAP            | 31      | Attach the belts to the Center and attach the Center to the MGN12 linear rail of the X axis.  This video is helpful: <https://www.youtube.com/watch?v=mJNCn72lQpU>
| Voron 2.4R2          | 132-138 | Route the belts.
| Voron 2.4R2          | 139-141 | Skip these, use the Tap instead.
| Voron 2.4R2          | 142     | Check your work.
| Voron TAP            | 32      |
| Voron TAP            | 33      | I had to avoid tucking the belts through the slots in the Front part, it interfered with the motion of the Tap.
| Voron TAP            | 34      |
| Stealthburner        | 1-10    |
| Stealthburner        | 11      | If you have a CAN kit using EBB SB2209/SB0000, use the Bigtreetech part: <https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/STL/Main_Body_EBB.stl>
| Stealthburner        | 12      |
| Stealthburner        | 13      | The 2024-06-23 kit uses a toolhead PCB (EBB SB2209 RP2040), so install the two threaded inserts for the optional toolhead PCB.
| Stealthburner        | 14      | For the 2024-06-23 kit: uses umbilical instead of cable chains so skip this page.
| Stealthburner        | 15-16   |
| Stealthburner        | 17      | For the 2024-06-23 kit: BMG idler assembly may consist of three parts like the manual shows, or it may consists of just two parts.  As long as the shaft fits tightly and the gear spins freely it's probably ok.  ![](/images/BMG-Idler-Assembly-manual.png) ![](/images/BMG-Idler-Assembly-actual.jpg)
| Stealthburner        | 18-20   |
| Stealthburner        | 21      | The Drive Assembly may come as a single piece, with no assembly needed.  ![](/images/single-part-Drive-Assembly.jpg)
| Stealthburner        | 22-30   |
| Stealthburner        | 31-32   | For kits with umbilical, skip this part and these pages.  Later we'll attach the BTT "Cable Bridge" that replaces the stock Voron "Chain Anchor".
| Stealthburner        | 33      |
| Stealthburner        | 34      | If you have a CAN kit using EBB SB2209/SB000, use the Bigtreetech part: <https://github.com/bigtreetech/EBB/blob/master/EBB%20SB2240_2209%20CAN/STL/Cable_Cover_For_PCB_V1.1.STL>
| Stealthburner        | 35-42   |
| Stealthburner        | 43      | Some kits will come with multiple PTFE tubes, use the shorter one with ~4 mm OD and ~2 mm ID.
| Stealthburner        | 44-54   |
| Stealthburner        | 55      | Discard the half of the fan housing that doesn't have the fan motor and rotor mounted on it.
| Stealthburner        | 56      | Don't screw in the screws yet, they'll come as part of the SB2209.
| EBB SB2209           | 2       | Install the SB0000 on top of the fan, then screw in the screws.
| EBB SB2209           | 3-4     | Set the SB2209 jumper for the voltage shown on your fans, mine were all 24V.
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
| EBB SB2209           | 20-24   |
| EBB SB2209           | 25-29   | Flash the EBB SB2240.  I had to unplug USB, press and hold BOOT, and reconnect USB in order to get it into bootloader mode, clicking the RST button did not work.
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
| Voron 2.4R2          | 174-179 | Skip these pages, the Formbot kit uses a Manta M8P control board instead.  Follow the instructions here instead: <https://docs.vorondesign.com/build/electrical/v2_m8p_wiring.html>
| Formbot Wiring guide | 1-4     | For older (non-CAN) kits: Mount the components as shown on the image, note that is the 350x350 so if you build a smaller printer it will be tighter. There's a picture further down in this guide with what is what.
| Voron 2.4R2          | 180-183 | Wire up the 24V PSU.  Test it before connecting 24V to anything.
| Voron 2.4R2          | 184-185 |
| Voron 2.4R2          | 186-189 | Skip these pages, the kit does not include Wago clamps.
| Voron 2.4R2          | 190-191 | Skip these pages, the kit does not include a 5V PSU or a Raspberry Pi.
| Voron 2.4R2          | 192-193 | Skip these pages, the kit does not include an Octopus control board.  Follow the instructions here instead: <https://docs.vorondesign.com/build/electrical/v2_m8p_wiring.html>
| Voron 2.4R2          | 194-199 | Older non-CAN, non-umbilical kit: mount cables in chains before mounting chains as it will be hard to do otherwise. Also don't forget the extra LED cable.  Newer kit with CAN & umbilical: skip these pages, the umbilical replaces the X and Y cable chains.
| Voron 2.4R2          | 200     | The B-motor cable is routed in the 2020 grove under the gantry and held in place with a plastic cover instead of zipties.  Trim the plastic cover to length.  ![](/images/A_B_motor_cable.jpeg)
|                      | 201-202 | Mount the two ends without the chain attached.  Adjust the number of links in the Z cable chain to get it to the correct length.  Open the gates/covers in the chain links before mounting.
|                      | 203     |
|                      | 204     | Skip this page if you have a newer kit with CAN/umbilical, it has no cables routed along the gantry.

Voron V2.4R2 & Formbot Wiring PDF: Attach cables between breakout board and controll board. When you have attached the last few cables you are mostly done with what you can do now, don't forgett to download and install the [Big tree tech PI version](https://github.com/bigtreetech/BTT-Pi) and from it flash the octopus board via the other smaller included SD-card.

[Software Configuration](https://docs.vorondesign.com/build/software/configuration.html)

Now follow the post build instructions to make sure you've done everything correct


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
