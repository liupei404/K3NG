# Interfacing to Logging and Contest Programs / K1EL Winkey 1 & 2 Interface Protocol Emulation

The keyer can be interfaced to logging and contest programs with the K1EL Winkey interface protocol emulation feature.  To enable, uncomment the following line:

    #define FEATURE_WINKEY_EMULATION

This defaults the code to Winkey 1 mode.  To enable K1El Winkey 2 interface protocol emulation functionality, uncomment this line in addition to the one above:

    #define OPTION_WINKEY_2_SUPPORT

If you want compile both the CLI and K1EL Winkey interface protocol emulation features and upload to a unit, uncommenting the line below will cause the unit to default to K1EL Winkey interface protocol emulation rather than the normal Command Line Interface mode at power up or reset.

    #define SERIAL_PORT_DEFAULT_WINKEY_EMULATION

With the K1EL Winkey interface protocol emulation feature enabled, if you hold down the command button (button 0) and reset or power up the unit, it will go into the non-default mode. (If the default is K1EL Winkey interface protocol emulation, it will go into Command Line Interface mode, and vice versa.)

You may need to disable some features to get both the CLI and K1EL Winkey interface protocol emulation features to fit into an Arduino Uno.  Other larger Arduino variants like the Mega can hold all of the features and options.

In K1EL Winkey interface protocol emulation mode the USB port will be set for 1200 baud.  The emulation is a 99.9% complete emulation, and it should work with most programs that support K1EL Winkey interfacing.  Many contest and logging programs  have been tested and work with all features me and others have tried.  (Win-Test works only with the keyer in Winkey 1 mode)

Currently the following functions are implemented:

* CW Sending (of course)
* Pause
* Key Down
* Unbuffered and Buffer Speed Setting
* Iambic A & B / Bug Mode Settings
* Ultimatic in normal, dit priority, and dah priority modes
* Farnsworth
* Pointer Operations
* Backspace
* Sidetone Frequency Settings (Winkey 1, 2, and custom frequencies)
* Paddle Reverse
* Paddle Watchdog
* Keying Compensation
* Dit to Dah Ratio
* Contest Wordspace
* Autospace
* PTT Lead, Tail, and Hang Time
* Speed Pot Setup and Query
* First Extension
* Software Paddle
* Weighting
* HSCW
* Serial Echoback
* Prosigns
* Dual transmitter keying lines
* Paddle Only Sidetone
* Memory button reporting
* Standalone Message Sending
* K1EL Winkey 2 memory querying and setting via EEPROM upload and download is not implemented.

The emulation functionality translates the K1EL Winkey interface protocol to native K3NG keyer functionality.  The K1EL Winkey “protocol” is a de facto standard and many programs support it, and developing an open standard protocol and getting all the major programs to support it would be a monumental undertaking.  So it made sense to merely emulate the existing protocol everyone else is talking.

SO2R operation has been run successfully with the N1MM contest program.

I have found to have this emulation work reliably with programs other than N1MM, you should disable the Arduino Automatic Software Reset as described here.  This is done by cutting the PC board trace labeled RESET-EN on the Arduino Uno board, or an alternate solution is to install a capacitor on the reset line.  I have found when some programs connect to the COM port, errant bytes are interpreted or received by the Arduino which trips up the protocol conversation and the program and keyer will not connect.  In this configuration the keyer will not reset when a program connects to the COM port and it will be “ready to talk” immediately when the program begins sending bytes.

If you do not disable Automatic Software Reset and experience issues, uncomment the following line:

    #define OPTION_WINKEY_DISCARD_BYTES_AT_STARTUP

This option will discard the first three bytes that arrive on the USB port.  This hack works for my hardware, but your mileage may vary.  The number of bytes discarded at start up can be set here:

    #define winkey_discard_bytes_startup 3

A side effect of disabling Automatic Software Reset is that you will need to manually hit the reset button when uploading new software to the Arduino.  The button should be pressed as soon as you “Binary sketch size: xxxxx bytes” message in the Arduino program.

If you attempt to use this emulation with other programs and have issues, please let me know and I’ll attempt to figure it out.  Serial port sniffer captures are very helpful in troubleshooting these issues.

N1MM exhibits a minor bug in the Send CW (CTRL K) window.  If you hit the Tab key, N1MM sends a 0x09 byte to the keyer which is actually the PinConfig command.  The next keystroke that is sent will be interpreted as an argument for this command and will alter the pin configuration and sidetone operation.  If you accidentally hit the Tab key and the keyer stops keying the transmitter, or the sidetone is operational is toggled, re-initialize the Winkey interface in N1MM to restore the keyer back to proper operation.  However, never fear, there is a workaround in the code for this bug.  Uncomment this line:

    #define OPTION_N1MM_WINKEY_TAB_BUG_WORKAROUND

Note this option breaks SO2R functionality in N1MM, but if you’re only going to be using one rig it will work fine.  I offered to give the N1MM team details on the bug, however my offer was ignored.  But I digress.

Despite the claims, the N1MM program is not open source.  If you request the source code it may be given to you and you can’t redistribute it or fork the code.  That’s called freeware and beg-for-the-source.  Not that there’s anything wrong with that, just don’t call it open source.  But I digress.  This keyer is compatible with both N1MM classic and N1MM Plus, despite my polite requests to be listed on the hardware compatibility page which have been ignored.  But I digress.  I seem to digress a lot, don’t I?

If you would like to use RUMlog or RUMped activate OPTION_WINKEY_FREQUENT_STATUS_REPORT.  Both programs like to have very frequent status bytes back from the Winkey host in order to send code properly.

If you’re using Wintest, active OPTION_WINKEY_2_HOST_CLOSE_NO_SERIAL_PORT_RESET.