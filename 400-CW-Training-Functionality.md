Under Construction....

The K3NG Arduino keyer has a training module, which at the time of this writing is evolving.  Currently it supports these training modes:

US Callsign Copying
Wordsworth

There are plans to add random code group copying, international callsign copying, and interactive contest exchange training.  Currently the training functionality is command line interface (CLI) based, however there a plans to make several of the modes that don't require the serial interface/CLI available in command mode.

To 

    #define FEATURE_TRAINING_COMMAND_LINE_INTERFACE

    #define OPTION_WORDSWORTH_CZECH
    #define OPTION_WORDSWORTH_DEUTSCH
