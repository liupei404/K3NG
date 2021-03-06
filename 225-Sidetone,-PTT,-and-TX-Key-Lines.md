### Sidetone Line

The sidetone line normally outputs square wave sidetone for driving a speaker.  Sidetone can be disabled on transmit using the command mode O command, the \O command line interface (CLI) command, or CTRL-O on a PS2/USB keyboard.  This function is for transmitters that generate their own sidetone.

The sidetone frequency can be adjusted using the F command in command mode or the \F CLI command.

If you wish to have a logic high / low level to key an external sidetone oscillator rather than a square wave output, uncomment this line in your features file:

    #define OPTION_SIDETONE_DIGITAL_OUTPUT_NO_SQUARE_WAVE

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

For testing purposes the PTT line can be manually toggled on and off using the \u CLI command.

If your CW transmitter keys up when the CW line is keyed (or you are not going to use multi-transmitter support), there is probably no need to use the PTT line.

If you do not need the PTT lines and wish to use the Arduino pins for another function such as a transmitter keying line, simply set the pin number to zero, as so:

    #define ptt_tx_1 0
    #define ptt_tx_2 0

PTT and TX key lines can be inhibited with the FEATURE_PTT_INTERLOCK function.  The PTT interlock pin is defined on this line:

    #define ptt_interlock 0

When the input is taken high, the PTT and TX key lines will not go active.

The active and inactive states of the PTT lines can be changed in your settings file with these lines:

    #define ptt_line_active_state HIGH
    #define ptt_line_inactive_state LOW

Starting in version 2018.03.11.01, PTT lead and tail times are stored in EEPROM and can be changed at runtime using extended commands.  (Extended commands are available if OPTION_EXCLUDE_MILL_MODE is not defined.  These commands are not available with the NanoKeyer, or Nano or Uno based keyers).

    \:pl <tx_number> <time_in_mS> - set PTT lead time
    \:pt <tx_number> <time_in_mS> - set PTT tail time
    \:timing - show all current timing settings

Timing Command Output

    \:timing
    Timings (mS)
    
    PTT
    TX      Lead    Tail
    --      ----    ----
    1       0       100
    2       0       10
    3       0       10
    4       0       10
    5       0       10
    6       0       10

If you do not have extended commands, the PTT lead and tail times are taken from the settings in the setting file and are written to EEPROM at first boot up.  If you need to change the timings, edit the settings file, recompile, and do a "factory reset" at boot up (squeeze both paddles and reset).

There is a PTT input line which manually activates PTT independent of CW keying.  This pin is defined in the pins file:

    #define ptt_input_pin 0

The logic active and inactive states can be changed in the settings file:

    #define ptt_input_pin_active_state LOW
    #define ptt_input_pin_inactive_state HIGH

The PTT input line also triggers the optional TX/RX [Sequencer] (https://github.com/k3ng/k3ng_cw_keyer/wiki/383-Feature:-Sequencer) functionality.

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

The active and inactive states of the TX lines can be changed in your settings file with these lines:

    #define tx_key_line_active_state HIGH
    #define tx_key_line_inactive_state LOW

### Dit and Dah Pins

If you need separate pins to indicate dits and dah, the pins can be defined here:

    #define tx_key_dit 0
    #define tx_key_dah 0

### TX Disable / Enable

The transmit line can be disabled and enabled using the \i CLI command or I command in command mode.  The equivalent PS2 keyboard command is CTRL-I.  This feature can be used for sending practice without keying the transmitter.

### PTT Interlock

For multi-transmitter operation in contests where only one station at a time is allowed to transmit, there is a PTT Interlock feature.

Enable this in your features file:

    #define FEATURE_PTT_INTERLOCK

Configure a pin in your pins file:

    #define ptt_interlock 0 

If desired, set this parameter in our settings file:

    #define ptt_interlock_active_state HIGH

When the ptt_interlock pin is taken to the active state, the keyer will not activate PTT.

### TX Inhibit and Pause / Contest Station Interlock Controllers

The keyer has two pins that can be interfaced with contest station interlock controllers (like [this one](https://github.com/k3ng/k3ng_station_interlock) ) to control transmitting.

The input pin tx_inhibit_pin, when taken active, will cause the keyer to stop transmitting and dump any buffered characters.  The input pin tx_pause_pin, when taken active, will also cause the keyer to stop transmitting but will preserve any buffered characters and resume sending them after the tx_pause_pin is taken inactive.

The pins are defined in your pins file:

    #define tx_inhibit_pin 0
    #define tx_pause_pin 0

...and the active and inactive states are defined in your settings file:

    #define tx_inhibit_pin_active_state LOW
    #define tx_inhibit_pin_inactive_state HIGH
    #define tx_pause_pin_active_state LOW
    #define tx_pause_pin_inactive_state HIGH 

### PTT Hold Active With Buffered Characters

When activated, the keyer will hold the current PTT line active if there are characters buffered, such as when characters are typed ahead in the CLI, or if the Winkey emulation has characters buffered.  This functionality can be activated and deactivated with the \" CLI command, or with the Winkey PINCONFIG command (bit 0), which is usually implemented in logging and contest programs with a radio button labeled PTT.

(Note that prior to version 2018.04.29.01 this function was optionally compiled in using OPTION_KEEP_PTT_KEYED_WHEN_CHARS_BUFFERED.  That option has been deprecated.)