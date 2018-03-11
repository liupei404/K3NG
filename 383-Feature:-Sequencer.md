# TX/RX Sequencer

## Introduction

The K3NG Arduino CW keyer has TX/RX sequencer output functionality.  This is useful for stations that have devices external to transceivers such as linear amplifiers, LNAs, and T/R switches.  Proper sequencing and timing during T/R switching is often crucial to avoid equipment damage.

The keyer offers five sequencer outputs, in addition to the [PTT lines](https://github.com/k3ng/k3ng_cw_keyer/wiki/225-Sidetone,-PTT,-and-TX-Key-Lines).  A PTT line can be configured for each transmitter.  The five sequencer outputs are transmitter independent.  Presumably with the right settings sequencer outputs could be split up between different transmitters and TX/RX chains.

## Theory of Operation

This admittedly rudimentary ASCII art timing diagram explains the timing relationship of the PTT, sequencer, and TX key lines, or at least a typical use case.

            +------------------------------------+
            |                                    |
    ptt ----+                                    +------------------

              +--------------------------------+
              |                                |
    seq1------+                                +--------------------

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

                         +-------------+
                         |             |
    tx_key---------------+             +----------------------------


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



## Disclaimer

Improper timing of TX/RX switching equipment may cause damage to equipment.  You must determine if this functionality fits your use case, and configure, test, and implement it yourself.  If you use this functionality, you do so at your own risk. 
