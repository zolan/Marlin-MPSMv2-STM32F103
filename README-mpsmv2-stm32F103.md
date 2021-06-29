# The Important Information

## Fix For 8 Second Reboot

This one is a really dirty fix but it fixes the reboot which was my first major problem.

It is in Marlin/src/pins/stm32f1/pins_MALYAN_M200.h

Huge thanks to reddit user subzee_ch, I learned that despite everyone saying that it was important to disable the watchdog, the thing that actually fixes this problem is to NOT disable the watchdog.   I'm certain this is not a great all-around fix that should be added to the main line repo but it was necessary for my printer.

## Base settings.

First thing, the Configuration.h and Configuration_adv.h are from the config repo Malyan/M200.  That is the base config I started with.

## Custom changes.

### Don't disable X/Y/Z

This was causing my steppers to not move at all.

### Enable Features

I really wanted the ability to store to EEPROM and to have Mesh bed leveling so I added those.  Also add the RESTORE_LEVELING_AFTER_G28 for good measure.  I also set the MESH_INSET to 15 instead of 10.  If you aren't worried about mesh bed leveling then forget about it.  But it is soooooo awesome...

### Cold Extrusion / Lengthy Extrusion

This actually threw me off for a stupid amount of time because I wasn't even aware it was a thing.  I thought my E stepper wasn't working but it was cold extrusion protection turned on.   I'm not going to extrude cold so I just disabled it.  It was super annoying.

### Invert Some Axises

Apparently these settings are always fairly specific to your printer.  You may need to tweak them on your printer but these settings work for me.

### Set The Steps Per Unit

This is also very specific to your printer.  There are two different types of steppers these printers came with.  Once again I got the oddball one.  See (https://www.mpselectmini.com/howto/steps_per_unit_mm).

*IMPORTANT NOTE:* I have since changed the Z axis in my configs because I replaced my Z motor with a NEMA17 and it also has an 8mm lead screw now.   So if you don't have that upgrade you'll need to change it back appropriately.

### Custom Printer Name

You will definitely want to change this.

### PID Settings

I really was tired of having to re-autotune after flashing.  So I just put the settings in the config.  You should always clear EEPROM and PID Autotune anyway so if you get different numbers you can customize yours here like I did.

### Host Action Commands

This one is dumb.   Octoprint was 'info-level warning' me that this wasn't enabled and I didn't want to disable those notifications so I just enabled it.


## Compiling

Sorry.  I'll try to come back here and fill this bit in.   I used Arduino and some STM32 libraries.  I couldn't get it to work on windows so I actually ran it on my RPi via X11 forwarding and stuff.  I remember there was something like a 'Printer Boards' and then I believe I chose the Malyan M200 v1.... ??

I will try to spend some time reconstructing what I did in the future so you can just follow along.
