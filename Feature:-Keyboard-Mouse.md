# PS2 / USB Keyboard Interface

A common PS2 or USB PC keyboard can be interfaced with the keyer to create a computerless CW keyboard.  The two types of keyboards use different libraries, so read carefully how to install and configure the proper libraries.

## PS2 Keyboard

1.  Download the modified PS2Keyboard library files from GitHub K3NG_PS2Keyboard.h and K3NG_PS2Keyboard.cpp).  Create a directory in your sketchbook library directory called K3NG_PS2Keyboard (i.e. \Arduino Sketchbook\libraries\K3NG_PS2Keyboard\)and place the two files in there.

2.  Uncomment the following line in the K3NG Arduino Keyer code:
.

    #define FEATURE_PS2_KEYBOARD PS2

3.  Connect up a PS2 keyboard to your Arduino.  Details on the pinouts of a PS2 keyboard connector can be found here.

Note that the PS2 keyboard data line can be relocated to other pins if desired, but the keyboard clock line must remain at pin 3 as that pin has special functionality for interrupt operation which is required by the PS2 keyboard library code.

4.  If you are using an international non-US keyboard, keyboard mappings can be chosen in K3NG_PS2Keyboard.h:
.

    #define OPTION_PS2_KEYBOARD_US
    #define OPTION_PS2_KEYBOARD_GERMAN
    #define OPTION_PS2_KEYBOARD_FRENCH

The French and German keyboard mappings may not be 100% correct and may need some adjustments.

## USB Keyboard

1. Download the Circuits@Home library on Github.  Install the library in a new directory in your Sketchbook libraries directory called USB_Host_Shield_20.

2. In k3ng_keyer.ino, uncomment this:
.
    #define FEATURE_USB_KEYBOARD

3. Uncomment these lines in k3ng_keyer.h:
.
    #include <hidboot.h>
    #include <usbhub.h>
    #include <Usb.h>

Arduino 1.6.x (and probably 1.5.x) has issues with these three lines, probably because Arduino now includes library files with the same names with the IDE package.  If you can’t get it to compile, try Arduino 1.0.x.  For me it compiles no problem with Arduino 1.0.5.

In order to connect the USB keyboard, you need hardware with a host USB port.  This can be accomplished several ways:

1. Get a Circuits@Home USB Shield.

2. Get an Arduino Mega ADK.  (Note that if you use the Mega ADK board, you must uncomment “#define BOARD_MEGA_ADK” in the library avrpins.h file.)

3. Get a Sparkfun USB Host Shield.

4.  Build your own USB host interface using the MAX3412 chip using any one of the above circuits as an example.

PS2 / USB Special Key Assignments:

* F1 through F12 – play memories 1 through 12
* Up Arrow – Increase CW Speed 1 WPM
* Down Arrow – Decrease CW Speed 1 WPM
* Page Up – Increase sidetone frequency
* Page Down – Decrease sidetone frequency
* Right Arrow – Dah to Dit Ratio increase
* Left Arrow – Dah to Dit Ratio decrease
* Home – reset Dah to Dit Ratio to default
* Tab – pause sending
* Delete – delete the last character in the buffer
* Esc – stop sending and clear the buffer
* Scroll Lock – Merge the next two characters to form a prosign
* Shift – Scroll Lock – toggle PTT line
* CTRL-A – Iambic A Mode
* CTRL-B – Iambic B Mode
* CTRL-D – Ultimatic Mode
* CTRL-E – Set Serial Number
* CTRL-G – Bug Mode
* CTRL-H – Hellschreiber Mode (requires FEATURE_HELL)
* CTRL-I – TX Line Disable/Enable
* CTRL-M – Set Farnsworth Speed (requires FEATURE_FARNSWORTH)
* CTRL-N – Paddle Revers
* CTRL-O – Sidetone On/Off
* CTRL-T – Tune
* CTRL-U – PTT Manual On/Off
* CTRL-W – Set WPM
* CTRL-Z – Autospace On/Off
* SHIFT-F1, F2, F3… – Program memory 1, 2, 3…
* ALT-F1, F2, F3… – Repeat memory 1, 2, 3…
* CTRL-F1, F2, F3… – Switch to transmitter 1, 2, 3…

USB Keyboard Only

* Keypad /  – Dit Paddle
* Keypad * – Dah Paddle

Keypad ENTER – Tune / Straightkey

Myself and others have experienced issues using just the Arduino USB client port +5V to power the Arduino and PS2 keyboard, with operation being erratic or the keyboard just not functioning at all.  This is due to computer USB ports not being able to supply enough current. The solution is simple: power the Arduino board directly using the power connector.

Some keyboards (like mini keyboards) may require a reset code sent to them in order to function correctly.  To enable this, in keyer_features_and_options.h uncomment:

    #define OPTION_PS2_KEYBOARD_RESET

## USB Mouse

Why connect a USB mouse to a keyer?  Because you can!

I added this feature on a whim after getting the USB keyboard code completed because the USB library supports mice and I wondered what it would be like to send code with a mouse.  The answer is it’s not great sending code with a mouse, however this feature code have  a practical application.  I connected a wireless mouse to the Arduino and was able to walk around the room sending code.  Undoubtedly you could use the guts of an old wireless mouse (I seem to go through one of these a year) and build a wireless paddle by mounting the electronics on a respectable paddle.

To enable the USB mouse functionality, install the USB library as described above in the USB Keyboard section and uncomment this line: #define FEATURE_USB_MOUSE

That’s it.  The left mouse button is dit, the right is dah, and the middle button is a straight key.

As of this writing I have not been able to get both the USB mouse and keyboard to work simultaneously in the code, however it is possible to run a PS2 keyboard and USB mouse, if you have a bigger Arduino, like the Mega, that has more memory to work with.

## USB HID Human Interface Device

This cool feature, which requires an Arduino Due or Leonardo, turns things around and lets you use your keyer as a keyboard for your computer.  (Yes, really.)  With it you can type up emails or whatever you like using your paddle.  Don’t try this with your off-the-shelf MFJ keyer or a pre-programmed proprietary keyer chip you bought, because they won’t do it.  LOL.  Open source rocks.  But I digress.

To enable this feature, uncomment FEATURE_CW_COMPUTER_KEYBOARD in keyer_features_and_options.h.

There are several special characters:

Return:     .-.-
Caps Lock:  -..---
Backspace:  6 to 9 dits
If you would like to hear a beeps when activating and deactivating caps lock, active OPTION_CW_KEYBOARD_CAPSLOCK_BEEP in keyer_features_and_options.h.

International keyboard mappings are in the works.  Currently there is one specific mapping available, OPTION_CW_KEYBOARD_ITALIAN in keyer_features_and_options.h.

This feature has been tested on both PCs and Macs.
