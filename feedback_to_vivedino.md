## Feedback for a 300x300 bought January 2024
### Positives with the Formbot kit
- The driver assembly shown on page 21 of the Stealthburner PDF came pre assembled which is nice.
- The neopixels on page 46 of the Stealthburner PDF came pre-soldered which was nice.
- Extra screws and nuts, huge plus.

### Larger issues
- The mounting of the DIN rails are different in the Voron setup. This was by far the most anoying thing in the whole build. I of course did not notice this before trying to mounting the A and B motor cables. I had then spent some time tidying thing up. Had to redo everything. Also one of the motors has to be turned for the PSU to fit. I have no idea why they choce to do it this way nor why the documentations is so poor. It just seems odd to not make this very clear and spend some time making sure the electrical configuration guide is very clear. In frustration I asked about this on the Discord but mostly got a "everyone knows the documentation from Formbot sucks". I hope the new kits will force an update.

    - This is what the Voron guide says on page, note where front and back is.
![](/images/voron_din_rails_mount.png)

    - This is the first page of the Formbot wiring, this is where your supposed to see that you've mounted the DIN-rails wrong some 100 page earlier.
![](/images/formbot_din_rail_mount.png)

    - This lead to everything needing remounting, you could probably smell the frustration
![](/images/din_rails_original_mount.jpeg)
![](/images/re-mounting.jpeg)
![](/images/Electrics_mounted.jpeg)

- Here's the problem with the motors on the 300x300 size. This i fixed by turning the motor 90 degrees so that the cables are pointed upwards. If you look closly this is done in the image above.
![](/images/motor_cables_not_fitting.jpeg)

- No mention to also drag neopixel cable, this you will probably find out after you've mounted everything making you have to redo the cable chains. If you have an octopus V1.1 it should be routed to the led pins, there should be three, this cable should be connected to the two on the USB-port side, with the 5V being closest to that side. They share ground with the rest of the board so that cable isn't needed.

### Minor issues
- In the kit the M3x10 BHCS screws are missing. I replaced these with the M3x12 BHCS. I was a bit affraid I might regrett this when they are needed later but so far I'm not sure where they are used. The Formbot-kit also seems to include a few extra of every screw which is very nice.

- On page 28 of the Stealthburner PDF, it's not clear which way the motor is supposed to be mounted, I did mine the same way the video linked on that page showed.

- The original CW2 latch broke, this is a known issue. I hope the Voron team redesigns this. If you have access to a printer, or a friend with a printer ask them to print a reinforced replacement (i printed [this one](https://www.printables.com/model/508340-updated-latch-for-voron-stealthburner-clockwork-2-])) before you even start. This could be PLA for now, it's good enough. Just make sure to print a new one in ABS later.
![](/images/broken_latch.jpeg
)
- One of the stepper-driver's heatsink was missing it's sticky thermal pad. This is a BTT QA issue and has nothing to do with Formbot. I solved this with some tape and thermal paste for now. I've ordered the correct tape to change it with whenever that arrives.
![](/images/missing_heat_sink_pad.jpeg)

- The split ground cable is a bit to short to make the routing nice, it also is to small to fit the screw so to make it fit one has to cut it.
![](/images/earth_too_short.jpeg)
![](/images/earth_too_small.jpeg)

- All screws in the kit are stainless steal, it's nice for everything but on page 27 of the TAP manual. The two M3x6 FHCS needs to be magnetic. I had to find my own and change these out. Later in feedback I learned that this is the R8 version of TAP and that it works with four magnets as well, this might have been the solution Formbot intended. I will probably change these next time I remove the extruder.
![](/images/replaced_screws.jpeg)

- The cable below is wrongly labled. It should say "Power to BED-Power". In later kits they've solved this with a sharpie.
![](/images/wrongly_labled_cable.jpeg)

- The cable chains are kind of bad quality. A few of my clips broke. As I plan to do a CAN-bus mod I don't care but if you're planning to keep them I would probably change these out.

