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

