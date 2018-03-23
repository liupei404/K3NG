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

Cees, PA3CVI, has published an [excellent Dutch manual](https://github.com/k3ng/k3ng_cw_keyer/files/1662287/Arduino.Handleiding.K3NG_CW_Keyer.pdf) and an [English Translation](https://github.com/k3ng/k3ng_cw_keyer/files/1839636/Arduino.Manual.K3NG_CW_Keyer_v5.1.pdf).





