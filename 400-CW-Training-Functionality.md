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

    C - Callsigns
    I - Callsigns - Interactive Practice
    W - Wordsworth

    X - Exit

# Callsigns

    Callsign Practice Menu

    I - International Callsigns
    U - US Callsigns
    E - European Callsigns
    C - Canadian Callsigns

    X - Exit

# Wordsworth

The Wordsworth method was created by George Allison, K1IG, and was described in the May 2017 issue of QST.  Andy Stewart, KB1OIQ, wrote code that was used to create the English word list used by this feature.  Wordsworth is like Farnsworth but instead of using increased letter spacing, Wordsworth uses increased word spacing.  The idea is to learn to head copy words and recognize the entire word as one unit rather than copying individual letters and assembling them into a word, much like we all do with spoken language.

    Wordsworth Menu

    2 - Two Letter Words
    3 - Three Letter Words
    4 - Four Letter Words
    N - Names
    Q - QSO Words
    M - Mixed

    O - Set Wordspace
    W - Set WPM
    R - Set Repetition

    X - Exit

    WPM:27 Wordspace:8 Effective WPM:17 Repetition:3


The default language for the Wordworth practice is English, however multi-language support is in progress.  There is are Czech and Norwegian translations and at the time of this writing a German translation is in progress.  To enable a translation, uncomment one of these lines in your features file:

    #define OPTION_WORDSWORTH_CZECH
    #define OPTION_WORDSWORTH_NORSK
    #define OPTION_WORDSWORTH_DEUTSCH
