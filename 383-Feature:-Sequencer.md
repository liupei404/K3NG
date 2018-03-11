# TX/RX Sequencer

## Introduction

The K3NG Arduino CW keyer has TX/RX sequencer output functionality.  This is useful for stations that have devices external to transceivers such as linear amplifiers, LNAs, and T/R switches.  Proper sequencing and timing during T/R switching is often crucial to avoid equipment damage.

The keyer offers five sequencer outputs, in addition to the [PTT lines](https://github.com/k3ng/k3ng_cw_keyer/wiki/225-Sidetone,-PTT,-and-TX-Key-Lines).  A PTT line can be configured for each transmitter.  The five sequencer outputs are transmitter independent.  Presumably with the right settings sequencer outputs could be split up between different transmitters and TX/RX chains.

## Theory of Operation

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

The 
