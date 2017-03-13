_This code is currently under construction_

A 3x4 or 4x4 membrane keypad can be substituted for the pushbutton memory switches,
but the MEMORY buttons can be retained and used with no effects on the
COMMAND/MEMORY functions.

By removing the MEMORY switches, the pushbuttons and 1k resistors can be eliminated.
The 10k resistor to +5 vdc is still used and the COMMAND pushbutton (button 0) switch is
retained.

To use a 3x4 or 4x4 keypad: In “features and options.h”, uncomment the proper keypad
and comment out the unused one.

Only the 1 through 0 buttons are used, (0 is for memory 10) If using a 4x4 keypad, the “A,
B, C, D #, *” keys could be used for any number of functions. Likewise, the “#, *” buttons
can be programmed to use the 11 and 12 memories on the 3x4 keypad or another function.
Just follow the SWITCH/CASE statements in the KeyPad_use() subroutine. I
programmed the “C” key to put the keyer into COMMAND MODE. To exit that mode,
push the COMMAND button or send an “X” on the key. The COMMAND_MODE()
subroutine does not look at the keypad, so pushbutton 0 or keyed “X” must be used.
All 12 memories can be used with the keypad and all memories appear to respond to
MEMORY MACROS.

In the CASE statements, unused keys are programmed to “beep-boop” to indicate this is an
unused key or unused keys can be commented out.

The code shows the proper OUTPUT pins on the Arduino Mega 2560 to use with either
keypad and the ROW/COLUMN pins on the keypads.

![](https://cloud.githubusercontent.com/assets/3332720/23837631/76783c4c-0761-11e7-8418-6713ed5ee172.png)

_Code and wiki text contributed by W0XR_