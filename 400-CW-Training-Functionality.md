# Introduction

Under Construction....

The K3NG Arduino keyer has a training module, which at the time of this writing is evolving.  Currently it supports these training modes:

US Callsign Copying
Wordsworth

There are plans to add random code group copying, international callsign copying, and interactive contest exchange training.  Currently the training functionality is command line interface (CLI) based, however there a plans to make several of the modes that don't require the serial interface/CLI available in command mode.

To enable the command line based training, uncomment this line in you features file:

    #define FEATURE_TRAINING_COMMAND_LINE_INTERFACE

To access the CW training module, in the command line interface execute the \K command and you will see this menu:

    CW Training Menu
    U - US Callsigns
    W - Wordsworth
    X - Exit

# US Callsign

# Wordsworth

The Wordsworth method was created by George Allison, K1IG, and was described in the May 2017 issue of QST.  Andy Stewart, KB1OIQ, wrote code that was used to create the English word list used by this feature.  Wordsworth is like Farnsworth but instead of using increased letter spacing, Wordsworth uses increased word spacing.  The idea is to learn to head copy words and recognize the entire word as one unit rather than copying individual letters and assembling them into a word, much like we all do with spoken language.

    Wordsworth Menu

    2 - Two Letter Words
    3 - Three Letter Words
    4 - Four Letter Words
    N - Names
    Q - QSO Words
    M - Mixed
    S - Set wordspace
    W - Set WPM
    X - Exit

    WPM:25 Wordspace:12 Effective WPM:13


The default language for the Wordworth practice is English, however multi-language support is in progress.  There is a Czech translation and at the time of this writing a German translation is in progress.  To enable a translation, uncomment one of these lines in your features file:

    #define OPTION_WORDSWORTH_CZECH
    #define OPTION_WORDSWORTH_DEUTSCH
