# Welcome to the k3ng_cw_keyer wiki!

Look to the right for documentation and help topics ---->


_(Like most things in the open source world, this wiki is under construction / evolving.  If you would like to volunteer to help make it better, your assistance would greatly appreciated and your name and callsign would be immortalized as a supporter of this project.)_



***

The K3NG Keyer is an open source [Arduino](http://www.arduino.cc/) based CW (Morse Code) keyer with a lot of features and flexibility, rivaling commercial keyers which often cost significantly more.  The code can be used with a full blown Arduino board or an AVR microcontroller chip can be programmed and used directly in a circuit.  This keyer is suitable as a standalone keyer or for use permanently installed inside a rig, especially homebrew QRP rigs.  It’s open source code so you can fully customize it to fit your needs and also perhaps learn from it or find coding ideas for other projects.  

A circuit board and parts kits called the [nanoKeyer](http://nanokeyer.wordpress.com/) is available from DJ0MY, and Hamshop offers a kit called [Open CW Keyer](http://www.hamshop.cz/open-cw-keyer-c27/open-cw-keyer-i196/) which uses this software. [RemoteQTH](http://remoteqth.com/) also offers the [Open Interface](http://remoteqth.com/open-interface.php) which runs this code.

## Features

* CW speed adjustable from 1 to 999 WPM
* Up to six selectable transmitter keying lines
* Programming and interfacing via USB port (“command line interface”)
* [USB or PS2 Keyboard Interface](https://github.com/k3ng/k3ng_cw_keyer/wiki/Feature:-Keyboard-&-Mouse#ps2--usb-keyboard-interface) for CW keyboard operation without a computer
* Logging and Contest Program Interfacing via K1EL Winkey 1.0 and 2.0 interface protocol emulation
* Optional PTT outputs with configurable lead, tail, and hang times
* Optional LCD Display – [Classic 4 bit mode](http://arduino.cc/en/Tutorial/LiquidCrystal) , [Adafruit I2C RGB](http://ladyada.net/make/rgblcdshield/) display and [I2C Character Backpack](https://www.adafruit.com/product/292) or [YourDuino I2C LCD Display](http://arduino-info.wikispaces.com/LCD-Blue-I2C)
* Up to 12 memories with macros
* Serial numbers
* CW keyboard (via a terminal server program like Putty or the Arduino Serial program)
* [Speed potentiometer](https://github.com/k3ng/k3ng_cw_keyer/wiki/Feature:-Speed-Control) (optional – speed also adjustable with commands)
* [QRSS and HSCW](https://github.com/k3ng/k3ng_cw_keyer/wiki#qrss-slow-speed-cw)
* [Beacon / Fox mode](https://github.com/k3ng/k3ng_cw_keyer/wiki#beacon-mode)
* [Iambic A and B](https://github.com/k3ng/k3ng_cw_keyer/wiki#iambic-modes)
* [Straight key support](https://github.com/k3ng/k3ng_cw_keyer/wiki#straight-key-support)
* [Ultimatic mode](https://github.com/k3ng/k3ng_cw_keyer/wiki#ultimatic-mode)
* [Bug mode](https://github.com/k3ng/k3ng_cw_keyer/wiki#bug-mode)
* [CMOS Super Keyer Iambic B Timing](https://github.com/k3ng/k3ng_cw_keyer/wiki#cmos-super-keyer-timing)
* [Paddle reverse](https://github.com/k3ng/k3ng_cw_keyer/wiki#paddle-reverse)
* [Hellschreiber mode](https://github.com/k3ng/k3ng_cw_keyer/wiki#hellschreiber) (keyboard sending, memory macro, beacon)
* Farnsworth Timing
* Adjustable frequency sidetone
* Sidetone disable / sidetone high/low output for keying outboard audio oscillator
* [Command mode](https://github.com/k3ng/k3ng_cw_keyer/wiki/Feature:-Command-Mode) for using the paddle to change settings, program memories, etc.
* Keying Compensation
* [Dah to Dit Ratio adjustment](https://github.com/k3ng/k3ng_cw_keyer/wiki#cw-dah-to-dit-ratio-adjust)
* Weighting
* [Callsign receive practice](https://github.com/k3ng/k3ng_cw_keyer/wiki#receive-callsign-practice)
* Send practice
* Memory stacking
* [“Dead Operator Watchdog”](https://github.com/k3ng/k3ng_cw_keyer/wiki#dead-operator-watchdog)
* [Autospace](https://github.com/k3ng/k3ng_cw_keyer/wiki#autospace)
* Wordspace Adjustment
* [Pre-configured and Custom Prosigns](https://github.com/k3ng/k3ng_cw_keyer/wiki#prosigns)
* Non-volatile storage of most settings
* Modular code design allowing selection of features and easy code modification
* Non-English Character Support
* [CW Receive Decoder](https://github.com/k3ng/k3ng_cw_keyer/wiki#cw-decoder)
* [Rotary Encoder Speed Control](https://github.com/k3ng/k3ng_cw_keyer/wiki/Feature:-Speed-Control#mayhew-labs-led-ring)
* [Sleep Mode](https://github.com/k3ng/k3ng_cw_keyer/wiki#sleep-mode)
* [USB Mouse Support](https://github.com/k3ng/k3ng_cw_keyer/wiki/Feature:-Keyboard-&-Mouse#usb-mouse)
* [Mayhew LED Ring Support](https://github.com/k3ng/k3ng_cw_keyer/wiki/Feature:-Speed-Control#mayhew-labs-led-ring)
* [Alphabet Sending Practice](https://github.com/k3ng/k3ng_cw_keyer/wiki#alphabet-code-practice-mode)
* QLF / “Messy” Straight Key Emulation
* [USB Keyboard HID](https://github.com/k3ng/k3ng_cw_keyer/wiki/Feature:-Keyboard-&-Mouse#usb-keyboard) (Human Interface Device) Interface (Keyer = keyboard for your computer)
* [TX/RX Sequencer](https://github.com/k3ng/k3ng_cw_keyer/wiki/383-Feature:-Sequencer)
* [Training Module](https://github.com/k3ng/k3ng_cw_keyer/wiki/400-CW-Training-Functionality)

## Videos
The K3NG Keyer has been feature in the following videos.
* [K3NG Arduino CW Keyer](https://youtu.be/bb-Y1aKlHXY)
* [nanoKeyer - K1EL Winkeyer compatible CW contest keyer (Arduino based)](https://youtu.be/B6_KfQ0tk60)
* [CW keyer OZ1JHM Hjalmar Skovholm Hansen](https://youtu.be/XHd9UAVJOLY)
* [K3NG Keyer on ATmega328 #1](https://youtu.be/D_-1-UKfcJA)

## Building
Check the following pages for information on constructing your own keyer.
* [Schematics](https://github.com/k3ng/k3ng_cw_keyer/wiki/Build:-Schematic)
* [Wiring Instructions](https://github.com/k3ng/k3ng_cw_keyer/wiki/Wiring-the-Keyer)
* [Configuring the Software](https://github.com/k3ng/k3ng_cw_keyer/wiki/Configuring-Your-Keyer)

Also check out [KF4BZT's article](https://kf4bzt.wordpress.com/2015/08/06/arduino-cw-keyer-project/) for lots of hints on working with the schematic for beginners and working with the components including lots of pictures.

Jmatonis has published on [Thingiverse a 3D model of his keyer enclosure](https://www.thingiverse.com/thing:2399311).

Cees, PA3CVI, has published an [excellent Dutch manual](https://github.com/k3ng/k3ng_cw_keyer/files/1662287/Arduino.Handleiding.K3NG_CW_Keyer.pdf) .

### CW Dah to Dit Ratio Adjust

The CW dash length to dot length ratio can be adjusted using the J command in command mode.  Upon entering the J command you will hear a repeating dit dah.  Use the left and right paddles to shorten or lengthen the dah.  Squeeze both paddles to exit the weight adjust command.  After that you can enter X or press the command button to exit command mode.

The ratio can also be adjusted in the command line interface using the \j command.  \j300 sets the keyer for a normal 3:1 ratio, \j250 would set it for a 2.5:1 ratio, for example.

### Paddle Reverse

The command mode N command switches the left and right paddles.  The equivalent function in the CLI is \n and using the PS2 keyboard it’s CTRL-N.

### Tune Mode

The command mode T command or command line interface \t command goes into tune up mode.  In the PS2 keyboard, use CTRL-T.

### TX Disable / Enable

The transmit line can be disabled and enabled using the \i CLI command or I command in command mode.  The equivalent PS2 keyboard command is CTRL-I.  This feature can be used for sending practice without keying the transmitter.

### Autospace

The autospace feature can be toggled on and off with the Z command in command mode, the \z command in the command line interface, and CTRL-Z using the PS2 keyboard.  This feature “cleans up” manual sending a bit by automatically inserting a wordspace delay if the operator waits more than one dit after sending a dit or dah to paddle either paddle.  The autospace feature is activated by uncommenting this line:

    #define FEATURE_AUTOSPACE

### Wordspace Adjustment

Wordspace is the key up time in between words.  By default it is set for seven dit lengths by this line in keyer_settings.h:

    #define default_length_wordspace 7

This can be adjusted using the \y command line interface command.

### Dit and Dah Buffer Control

The dit and dah buffers can be turned on and off by adding this feature:

    #define FEATURE_DIT_DAH_BUFFER_CONTROL

The dit and dah buffers can be turned on and off using the command line interface \. and \- commands.  The settings are stored in nonvolatile memory.

### Keying Compensation

The keying compensation filter extends the time of both dits and dahs to compensate for older transmitters that are slow on the draw in QSK at higher speeds.  The inter-element key up times are reduced a corresponding amount of time.  The time in mS can be set here in keyer_settings.h:

    #define default_keying_compensation 0

Currently there is no command to adjust this at runtime, however the Winkey emulation will adjust this if it is set in the host application.

### First Element Extension Time

This feature makes the first dit or dah sent longer to compensate for slow T/R switches in rigs.  The time is set here in keyer_settings.h:

    #define default_first_extension_time 0

Currently there is no command to adjust this at runtime, however the Winkey emulation will adjust this if it is set in the host application.

### Prosigns

Custom prosigns can be sent using \+ in the CLI or in memories as a macro.  Several “hard wired” / common prosigns are available for various keys on the PS2 keyboard like =, -, &, etc. and the Sroll Lock key can be used to create custom prosigns on the fly.

If you are programming a memory in command mode using the paddle, the \+ macro can be used to create prosigns.  The \ is six dahs ( – – – – – – ) and + is didahdidahdit ( . – . – . ).  Common prosigns AR, BK, and SK are automatically recognized and do not need to be proceeded with a \+ macro, just send the prosign as you normally would (AR would be didahdidahdit, not didah didahdit).

### Receive Callsign Practice

In the command line interface the \k goes into callsign receive practice.  Random callsigns are sent, the user enters the received callsigns, and the keyer will tell the user if they were correct.

Currently this code produces only US callsigns.  I’ll be working on enhancements later to add other country callsigns, allow various user settings and adjustments, and variable speed based on the user’s accuracy.

This feature requires this to be uncommented:

    #define FEATURE_CALLSIGN_RECEIVE_PRACTICE 

### Dead Operator Watchdog

This feature turns off the transmit line after 100 consecutive dits or dahs.  It can be enabled by uncommenting this line:

    #define FEATURE_DEAD_OP_WATCHDOG

### Reset to “Factory” Defaults

To reset the keyer to defaults, depress both the left and right paddles and do a reset or power reset.  This will wipe out all memories and change all the settings back to defaults.

### Dit and Dah Pins

If you need separate pins to indicate dits and dah, the pins can be defined here:

    #define tx_key_dit 0
    #define tx_key_dah 0

### Banked Memory Buttons

A [method for banked memory switches](http://dl2sba.com/index.php?option=com_content&view=article&id=131:nanokeyer&catid=15:shack&Itemid=27#english) was created by DL2SBA and can be implemented by uncommenting:

    #define FEATURE_DL2SBA_BANKSWITCH

### Non-English Characters

To enable support for non-English characters (i.e. À, Ä, È, Ö, etc.), uncomment this line:

    #define OPTION_NON_ENGLISH_EXTENSIONS

If you need to customize the characters for your locality or language, modify the code in functions send_char() and convert_cw_number_to_ascii().  This support was added in version 2012011701 and currently works only with the command line interface and the K1EL Winkey interface protocol emulation.  Support for the PS2 keyboard is in the works.

### Sleep Mode

Sleep mode will put the unit to sleep after a certain amount of inactivity, in order to preserve battery power.  To enable the feature, uncomment this line:

    #define FEATURE_SLEEP

The inactivity timer is set here (the unit is minutes):

    #define go_to_sleep_inactivity_time 10

To wake the keyer after it goes to sleep, simply hit the left (normally dit) paddle.

### Command Mode Active LED

If you would like to have an LED activate when in command mode, define this pin and have it power an LED:

    #define command_mode_active_led 0

### Alphabet Code Practice Mode

The feature allows you to practice sending the alphabet.  To access it, go into command mode and send S on the paddle.  You’ll here a dit.  Send the letters in alphabetical order on the paddle: A, B, C, etc.  If you send the correct letter in succession, you’ll hear a beep.  If you send the wrong CW, the keyer will tell you with a boop sound.  If you make a mistake, try to send the character again.  To exit alphabetical sending practice, press the command button.

This feature is enabled by uncommenting:

    #define FEATURE_ALPHABET_SEND_PRACTICE

The code for this feature was provided by Ryan, KC2ZWM.




### Multiple Serial Ports

Some Arduino models like the Mega have multiple serial ports.  With this keyer code it is possible to run two serial ports simultaneously.  One port can run Winkey emulation, the other can run the Command Line Interface, or both can run the CLI.

To use this feature, enable FEATURE_COMMAND_LINE_INTERFACE_ON_SECONDARY_PORT in keyer_features_and_options.h.

This enables a Command Line Interface on a secondary serial port of your choosing, defined in keyer_settings.h:

    #define SECONDARY_SERIAL_PORT &Serial1
    #define SECONDARY_SERIAL_PORT_BAUD 115200

If you enable FEATURE_WINKEY_EMULATION and OPTION_PRIMARY_SERIAL_PORT_DEFAULT_WINKEY_EMULATION, the primary serial port will go into Winkey emulation mode at boot up. The primary serial port is also defined in keyer_settings.h:

    #define PRIMARY_SERIAL_PORT &Serial

If you hold down the command button at boot up, the primary serial port will switch to Command Line Interface mode.

To summarize some configuration combinations:

> FEATURE_COMMAND_LINE_INTERFACE (only) – CLI on the primary port (“Serial0”)
>
> FEATURE_WINKEY_EMULATION (only) – Winkey on the primary port (“Serial0”)
>
> FEATURE_COMMAND_LINE_INTERFACE+FEATURE_WINKEY_EMULATION+ OPTION_PRIMARY_SERIAL_PORT_DEFAULT_WINKEY_EMULATION: Winkey on the primary port (“Serial0”) by default, hold command button at boot up for CLI
>
> FEATURE_COMMAND_LINE_INTERFACE+FEATURE_WINKEY_EMULATION: CLI on the primary port (“Serial0”) by default, hold command button at boot up for Winkey
>
> FEATURE_COMMAND_LINE_INTERFACE+FEATURE_WINKEY_EMULATION+ OPTION_PRIMARY_SERIAL_PORT_DEFAULT_WINKEY_EMULATION+FEATURE_COMMAND_LINE_INTERFACE_ON_SECONDARY_PORT: Winkey on the primary port (“Serial0”) by default, hold command button at boot up for CLI on primary port (“Serial0”), CLI on secondary port (Serial1) all the time
> 
> FEATURE_COMMAND_LINE_INTERFACE+FEATURE_COMMAND_LINE_INTERFACE_ON_SECONDARY_PORT: CLI on both primary port (“Serial0”) and secondary port (Serial1) all the time


## Miscellaneous Notes

Do not enable the potentiometer feature if you do not have a potentiometer connected, otherwise noise on the pin will falsely trigger speed changes.  Also, do not enable FEATURE_BUTTONS unless you have the corresponding resistors on the button pin connected.  If the analog button pin does not have +5 volts on it, the keyer will not start up as it thinks there is a button depression in progress.



