# Connecting the Keyer

## Primary Pins
Here are the main pins you need to connect up to get started:

**Left Paddle** – pin 2 – connect to your left paddle (grounding will send dits)

**Right Paddle** – pin 5 – connect to your right paddle (grounding will send dahs)

**Transmitter Key** – pin 11 – goes high for key down; use to drive a transistor to ground the TX key

**Sidetone** – pin 4 – this outputs square wave sidetone to drive a speaker (schematic coming out shortly for driving with a transistor).  The sidetone can be deactivated on transmit for transmitters that generate their own sidetone.

**The command button** – pin A1 and at least R7, see schematics and the Memory buttons section for expansion of this

**Memory buttons** - up to 12 memory buttons can be added to the command button. Add buttons and resistors R8, R9, R10, etc.  (You can do just a few memory buttons, all 12, or none at all. See schematics for details.

## Optional Pins
Additional pins you may be interested in for other functionality:

**PTT (push to talk)** - described in more detail in the wiki

**Additional TX Key lines** - add support for multi-transmitter capability

**Potentiometer Speed Control** – pin A0 – connect one end of the pot to +5V, the other end to ground, and connect the wiper to pin A0 to quickly adjust the speed

**Rotary Encode Speed Control** – no default pins are defined; two pins are required, defined by the following options in _keyer_pin_settings.h_:

    rotary_pin1 
    rotary_pin2

## Changing Pins
Almost all pins can be easily changed if desired in _keyer_pin_settings.h_. Be careful not to assign the same pin to multiple needs.

Please note the following exceptions:
* If using a PS2 keyboard, the clock pin must remain at pin 3 due to interrupt requirements. 
* If using an Adafruit I2c display, pins A4 and A5 are needed for I2C.