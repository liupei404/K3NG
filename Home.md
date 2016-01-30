Full documentation for the K3NG Arduino CW Keyer is located [here](http://blog.radioartisan.com/arduino-cw-keyer/). It is being moved over to the wiki, but this is not yet complete

***

The K3NG Keyer is an open source Arduino based CW (Morse Code) keyer with a lot of features and flexibility, rivaling commercial keyers which often cost significantly more.  The code can be used with a full blown Arduino board or an AVR microcontroller chip can be programmed and used directly in a circuit.  This keyer is suitable as a standalone keyer or for use permanently installed inside a rig, especially homebrew QRP rigs.  It’s open source code so you can fully customize it to fit your needs and also perhaps learn from it or find coding ideas for other projects.  

A circuit board and parts kits called the nanoKeyer is available from DJ0MY, and Hamshop offers a kit called Open CW Keyer which uses this software.  RemoteQTH also offers the Open Interface which runs this code.

## Features

* CW speed adjustable from 1 to 999 WPM
* Up to six selectable transmitter keying lines
* Programming and interfacing via USB port (“command line interface”)
* USB or PS2 Keyboard Interface for CW keyboard operation without a computer
* Logging and Contest Program Interfacing via K1EL Winkey 1.0 and 2.0 interface protocol emulation
* Optional PTT outputs with configurable lead, tail, and hang times
* Optional LCD Display – Classic 4 bit mode , Adafruit I2C RGB display or YourDuino I2C LCD Display
* Up to 12 memories with macros
* Serial numbers
* CW keyboard (via a terminal server program like Putty or the Arduino Serial program)
* Speed potentiometer (optional – speed also adjustable with commands)
* QRSS and HSCW
* Beacon / Fox mode
* Iambic A and B
* Straight key support
* Ultimatic mode
* Bug mode
* CMOS Super Keyer Iambic B Timing
* Paddle reverse
* Hellschreiber mode (keyboard sending, memory macro, beacon)
* Farnsworth Timing
* Adjustable frequency sidetone
* Sidetone disable / sidetone high/low output for keying outboard audio oscillator
* Command mode for using the paddle to change settings, program memories, etc.
* Keying Compensation
* Dah to Dit Ratio adjustment
* Weighting
* Callsign receive practice
* Send practice
* Memory stacking
* “Dead Operator Watchdog”
* Autospace
* Wordspace Adjustment
* Pre-configured and Custom Prosigns
* Non-volatile storage of most settings
* Modular code design allowing selection of features and easy code modification
* Non-English Character Support
* CW Receive Decoder
* Rotary Encoder Speed Control
* Sleep Mode
* USB Mouse Support
* Mayhew LED Ring Support
* Alphabet Sending Practice
* QLF / “Messy” Straight Key Emulation
* USB Keyboard HID (Human Interface Device) Interface (Keyer = keyboard for your computer)

## Videos
The K3NG Keyer has been feature in the following videos.
* [K3NG Arduino CW Keyer](https://youtu.be/bb-Y1aKlHXY)
* [nanoKeyer - K1EL Winkeyer compatible CW contest keyer (Arduino based)](https://youtu.be/B6_KfQ0tk60)
* [CW keyer OZ1JHM Hjalmar Skovholm Hansen](https://youtu.be/XHd9UAVJOLY)
* [K3NG Keyer on ATmega328 #1](https://youtu.be/D_-1-UKfcJA)

### Beacon Mode

In order to have the keyer go directly into beacon mode at power up or reset and stay in beacon mode, simply ground pin 2.  This is useful for keyers that are dedicated to beacon or fox service.

### Iambic Modes

To switch to Iambic A mode, use the A command in command mode or \a in the command line interface.

To switch to Iambic B mode, use the B command in command mode or \b in the command line interface.

(An explanation of Iambic A and B can be found [here](http://wb9kzy.com/modeab.pdf).)

### Straight Key Support

There are two ways to use a straight key with the keyer:

Go into straight key mode by holding down the right paddle when powering up or power resetting.  This places the keyer exclusively in straight key mode with very limited functionality.
Activate FEATURE_STRAIGHT_KEY in features_and_options.h and define pin_straight_key in keyer_pin_settings.h .  Grounding the pin with a straight key will give you straight key operation in parallel with paddle operation and still give you access to the all the normal keyer functionality.  (The straight key does not work in command mode, however it can be used to program memories when used with FEATURE_STRAIGHT_KEY. )

### Bug Mode

To go into bug mode, use the command mode G command or the command line \g command.

### Ultimatic Mode

To go into Ultimatic mode, use the command mode D command or the command line \d command.

### CMOS Super Keyer Timing

This is enabled by uncommenting this line in keyer_features_and_options.h:

    #define FEATURE_CMOS_SUPER_KEYER_IAMBIC_B_TIMING

And the default timing setting can be set in keyer_settings.h:

    #define default_cmos_super_keyer_iambic_b_timing_percent 33

CMOS Super Keyer Timing applies only to Iambic B mode.  Setting the timing percent to 0 (zero) is essentially pure Iambic B and 100 is pure Iambic A.  This function can be turned on and off at runtime using the command line interface \& command, and the timing percentage can be set using the \% command.  Settings for this are stored in nonvolatile memory.

### Sidetone Line

The sidetone line normally outputs square wave sidetone for driving a speaker.  Sidetone can be disabled on transmit using the command mode O command.  This is for transmitters that generate their own sidetone.

The sidetone frequency can be adjusted using the F command in command mode.

### PTT (“Push To Talk”)

The PTT pins go high whenever code is sent.  If it’s desired to have the PTT line go high before code is sent or stay high for a period of time after code stops being sent, these lines can be adjusted in keyer_settings.h:

    #define initial_ptt_lead_time_tx1 10
    #define initial_ptt_tail_time_tx1 10
    #define initial_ptt_lead_time_tx2 10
    #define initial_ptt_tail_time_tx2 10
    #define initial_ptt_lead_time_tx3 10
    #define initial_ptt_tail_time_tx3 10
    #define initial_ptt_lead_time_tx4 10
    #define initial_ptt_tail_time_tx4 10
    #define initial_ptt_lead_time_tx5 10
    #define initial_ptt_tail_time_tx5 10
    #define initial_ptt_lead_time_tx6 10
    #define initial_ptt_tail_time_tx6 10

The lead and tail times are in milliseconds, and these are set for each transmitter independently.  This feature is useful for driving T/R switches or older transmitters than need a little more time to get keyed up, or FM fox transmitters that need to have PTT keyed and sidetone pumped into the microphone line.

Hang time can be set by modifying this line in keyer_settings.h:

    #define default_ptt_hang_time_wordspace_units 0.0

PTT tail time is invoked when sending code automatically, such as via a memory play, the CLI, the PS2 keyboard, or Winkey interface emulation.  PTT hang time is invoked for manual sending using the paddle and is speed (wpm) dependent.

Note that if you activate PTT lead time, you should activate tail time as well, otherwise PTT lead time will be invoked before each dit or dah, significantly slowing down the sending speed.

Currently PTT lead, tail, and hang times can only be changed at runtime using the Winkey interface emulation.  (Let me know if you would like CLI commands to do this.)

For testing purposes the PTT line can be manually toggled on and off using the \u CLI command.

If your CW transmitter keys up when the CW line is keyed (or you are not going to use multi-transmitter support), there is probably no need to use the PTT line.

If you do not need the PTT lines and wish to use the Arduino pins for another function such as a transmitter keying line, simply set the pin number to zero, as so:

    #define ptt_tx_1 0
    #define ptt_tx_2 0

PTT and TX key lines can be inhibited with the FEATURE_PTT_INTERLOCK function.  The PTT interlock pin is defined on this line:

    #define ptt_interlock 0

When the input is taken high, the PTT and TX key lines will not go active.

### QRSS (Slow Speed CW)

QRSS mode can be activated using the command line \q command or in memory macros using the \q macro.  Both take the dit length in seconds (double digit number) as an argument.  For example: \q09 would put the keyer in QRSS mode with nine second long dits (and 27 second long dahs).

The \r command will switch back to regular CW speed mode in both the command line and in memories.

### HSCW (High Speed CW)

High speed CW can be accomplished by using the \w command line interface command or in memories as a macro.  Whereas the command mode speed adjustment and the speed potentiometer allow the speed to go up to a maximum of 60 WPM, the \w command will let you take it up to 255 WPM.

### Hellschreiber

The keyer will send Hellschreiber characters by placing it in Hellscreiber mode using the \h command in the serial command line interface or memory macros.  In the command line interface \c will return the keyer to CW mode and the \l (as in lima) memory macro will change back to CW.  While in Hellschreiber mode, the paddle will still send CW.  The Hellschreiber mode is intended mainly for beacons but works just fine for direct keyboard sending and is enabled with FEATURE_HELL in keyer_features_and_options.h.

![Hellschreiber copied from the keyer speaker into a laptop](https://radioartisan.files.wordpress.com/2011/03/k3ng-keyer-hell.png)

Hellschreiber Copied From the Keyer Speaker into a Laptop

Know of any commercial keyers that send Hellschreiber?  :-)  Keep reading.  There’s more.

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

### Multi-Transmitter Capability

This keyer supports multiple transmitters that can be selected using the \x CLI command, the CTRL-F1, F2, etc. key combinations on the PS2 keyboard, or using the hardware buttons (button1 hold, button2 hold, button3 hold, etc.).  Up to six transmitters can be configured, each with its own keying line and PTT line.  PTT lines are optional.  The configuration of the TX Key and PTT lines are here:

    #define tx_key_line_1 11
    #define tx_key_line_2 12
    #define tx_key_line_3 13
    #define tx_key_line_4 0
    #define tx_key_line_5 0
    #define tx_key_line_6 0

    #define ptt_tx_1 0
    #define ptt_tx_2 0
    #define ptt_tx_3 0
    #define ptt_tx_4 0
    #define ptt_tx_5 0
    #define ptt_tx_6 0

Setting a line to zero disables it.  At the very least you need one TX Key line defined.  Obviously, with the Arduino Uno, pins are at a premium and each features uses pins.  Larger Arduino platforms like the Mega offer more pins and more compiled-in functionality due to the larger memory space.

### Dit and Dah Pins

If you need separate pins to indicate dits and dah, the pins can be defined here:

    #define tx_key_dit 0
    #define tx_key_dah 0

### Banked Memory Buttons

A method for banked memory switches was created by DL2SBA and can be implemented by uncommenting:

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

