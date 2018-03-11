# TX/RX Sequencer

## Introduction

The K3NG Arduino CW keyer has TX/RX sequencer output functionality.  This is useful for stations that have devices external to transceivers such as linear amplifiers, LNAs, and T/R switches.  Proper sequencing and timing during T/R switching is often crucial to avoid equipment damage.

The keyer offers five sequencer outputs, in addition to the [PTT lines](https://github.com/k3ng/k3ng_cw_keyer/wiki/225-Sidetone,-PTT,-and-TX-Key-Lines).  A PTT line can be configured for each transmitter.  The five sequencer outputs are transmitter independent.  With the appropriate settings sequencer outputs could be split up between different transmitters and TX/RX chains.

## Theory of Operation

This admittedly rudimentary ASCII art timing diagram explains the timing relationship of the PTT, sequencer, and TX key lines, in a typical use case.

            +----------------------------+                     active
            |                            |
    ptt ----+                            +------------------   inactive

                         +-------------+                       active
                         |             |
    tx_key---------------+             +---------------------- inactive

              +--------------------------------+               active
              |                                |
    seq1------+                                +-------------- inactive

                +----------------------------+
                |                            |
    seq2--------+                            +----------------------

                   +-----------------------+
                   |                       |
    seq3-----------+                       +------------------------

                     +--------------------+
                     |                    |
    seq4-------------+                    +-------------------------

                       +-----------------+
                       |                 |
    seq5---------------+                 +--------------------------




## Compile Time Configuration

The sequencer pins are defined in your pins file:

    #define sequencer_1_pin 0
    #define sequencer_2_pin 0
    #define sequencer_3_pin 0
    #define sequencer_4_pin 0
    #define sequencer_5_pin 0

The active and inactive states of the pins can be changed in your settings file:

    #define sequencer_pins_active_state HIGH
    #define sequencer_pins_inactive_state LOW

To activate the sequencer functionality, uncomment this line in your features file:

    #define FEATURE_SEQUENCER

To be able to configure the sequencer timing, you need to have extended CLI commands.  This line must be disabled (commented out) in your features file, like so:

    //#define OPTION_EXCLUDE_EXTENDED_CLI_COMMANDS

## Hardware

It's highly recommended to use an Arduino Mega or equivalent.  The sequencer output pins can be used to drive bipolar transistors and interface with relays or amplifiers as needed.

## Run Time Configuration

Both PTT and Sequencer line timing can be configured at run time using extended commands:

    \:pl <tx_number> <time_in_mS> - set PTT lead time
    \:pt <tx_number> <time_in_mS> - set PTT tail time
    \:pa <sequencer_number> <time_in_mS> - PTT active to sequencer active time
    \:pi <sequencer_number> <time_in_mS> - PTT inactive to sequencer inactive time
    \:timing - show all current timing settings

The output of the timing command looks like this:

    \:timing
    Timings (mS)

    PTT
    TX      Lead    Tail
    --      ----    ----
    1       0       100
    2       0       0
    3       0       0
    4       0       0
    5       0       0
    6       0       0

    Sequencer
    #       PTT Active to Sequencer Active  PTT Inactive to Sequencer Inactive
    -       ------------------------------  ----------------------------------
    1                       25                              5
    2                       20                              10
    3                       15                              15
    4                       10                              20
    5                       5                               25

    Command Hints

    pl <transmitter> <mS>   Set PTT lead time
    pt <transmitter> <mS>   Set PTT tail time
    pa <#> <mS>             Set PTT active to Sequencer active time
    pi <#> <mS>             Set PTT inactive to Sequencer inactive time

This example setup is just an example and naturally you will need to adjust based on your equipment and requirements, however the setup above will yield timing like what is shown in the Theory of Operation section above.  For smooth operation, it's recommended that the PTT Tail Time exceed the longest PTT inactive to Sequencer inactive time.  Times of 0 to 255 mS can be configured.

## PTT Input

A PTT input pin can be configured to initiate PTT and the Sequencer sequence independent of CW keying.


    #define ptt_input_pin 0

The logic active and inactive states can be changed in the settings file:

    #define ptt_input_pin_active_state LOW
    #define ptt_input_pin_inactive_state HIGH

This pin is held high with an AVR internal pullup.  Taking the pin to its active state (LOW by default) will cause the active transmitter PTT line to go active (HIGH by default), and the sequencer pins to go active, according to configured delay times.

## Disclaimer

Improper timing of TX/RX switching equipment may cause damage to equipment.  You must determine if this functionality fits your use case, and configure, test, and implement it yourself.  If you use this functionality, you do so at your own risk. 
