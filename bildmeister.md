
# Modification of a Siemens BILDMEISTER Turnier FZ 2001

I recently got a Siemens BILDMEISTER Turnier FZ 2001 game console (AY-3-8500 based) which is dedicated to 
Siemens BILDMEISTER color TV sets and can be used after inserting an AV module to the TV set.
Controllers have a push button called "trick" each which, as long as pressed, will enable high-speed ball mode.

![board](/images/Siemens_BILDMEISTER_Turnier_FZ_2001_case.jpg)
![board](/images/Siemens_BILDMEISTER_Turnier_FZ_2001.jpg)
![board](/images/AV_modul.jpg)
![board](/images/AV_modul_back.jpg)

As i do not own this type of TV set and want to play the game on a regular TV i reversed and modded the circuit to interface to a SCART connector.

## pinout

![board](/images/din_6pin.png)
(the image shows pin orientation when looking onto the AV module).


| pin    |                                          |
|--------|------------------------------------------|
| 1      |  Vcc: +8,9V...10.3V                      |
| 2      |  Video                                   |
| 3      |  GND                                     |
| 4      |  TV/Action button == Vcc if game enabled |
| 5      |  n.c.                                    |
| 6      |  Audio - 2k7 to AY pin 3                 |
| shield |  console: n.c., module: GND              |

The video signal is not well compatible with standardized video inputs like SCART (75Ohm, 1Vpp).
Video voltage levels are too weak to produce a bright image, so the circuit needs a modification.
And the AY white signals (field, ball, left, right) and the sync signals are simply mixed together by a resistor each.
This will give no real white and signal gets brighter when paddle and field overlap.

I modified the video signal generation like this: voltage divider 2k2/1k connected to internal power (~7V == AY pin 4).
A diode to field, ball, left, right pulls up this voltage when signal shall be white. A diode to sync pulls down signal when H/V pulse is active.
The existing transistor (emitter follower) amplifies current and the video signal can be used as video signal.
I reduced the series resistor of 390Ohm to 100Ohm for better adaption to 75Ohm input impedance and brighter picture.

