# Serial Command Line Interface (CLI) / CW Keyboard

The keyer has a serial Command Line Interface (CLI) using the built in Arduino USB port or AVR serial port.  This is enabled by uncommenting this line in keyer_features_and_options.h:

    #define COMMAND_LINE_INTERFACE

Simply connect to your computer and use a terminal program such as the Arduino serial port program or Putty.  If you use the Arduino program, it’s recommended that you set it for carriage return (lower right).

To use the CW keyer functionality, simply type in what you want to send.  In the Arduino serial interface you will need to hit Enter to send the data to the keyer for it to start sending.  Programs like Putty will immediately send the characters and the keyer will send the code immediately as well.

Commands are preceded with a backslash (” \ “), the key above your Enter key (at least on US PC keyboards).  To see a help screen, enter backslash question mark ” \? ”  (no quotes).  The status command (\s) is a useful command for viewing various settings and seeing the contents of the memories.  If you enter a double backslash (“\\”), all sending buffers will be cleared and any memory sending will stop (this includes sending invoked by the PS2 keyboard or Winkey interface protocol emulation features).

### CLI Commands:

    \? Help
    \# Play memory #
    \a Iambic A mode
    \b Iambic B mode
    \c Switch to CW (from Hell)
    \d Ultimatic mode
    \e#### Set serial number to ####
    \f#### Set sidetone frequency to #### hertz
    \g Bug mode
    \h Switch to Hell sending
    \i Transmit enable/disable
    \j### Dah to dit ratio (300 = 3.00)
    \k Callsign receive practice
    \l## Set weighting (50 = normal)
    \m### Set Farnsworth speed
    \n Toggle paddle reverse
    \o Toggle sidetone on/off
    \p# Program memory #
    \q## Switch to QRSS mode, dit length ## seconds
    \r Switch to regular speed mode
    \s Status
    \t Tune mode
    \u Manual PTT toggle
    \v Toggle potentiometer active / inactive
    \w### Set speed in WPM
    \x# Switch to transmitter #
    \y# Change wordspace to # elements (# = 1 to 9)
    \z Autospace on/off
    \+ Create prosign
    \!## Repeat play memory
    \|#### Set memory repeat (milliseconds)
    \* Toggle paddle echo
    \^  Toggle wait for carriage return to send CW / send CW immediately
    \~ Reset unit
    \& Toggle CMOS Super Keyer Timing on/off
    \%## Set CMOS Super Keyer Timing %
    \. Toggle dit buffer on/off
    \- Toggle dah buffer on/off
    \: CW send echo inhibit toggle
    \{ QLF mode on/off
    \> Send serial number, then increment
    \< Send current serial number
    \( Send current serial number in cut numbers
    \) Send serial number with cut numbers, then increment

![K3ng keyer CLI](http://radioartisan.files.wordpress.com/2011/03/k3ng-keyer-command-line-interface.png)