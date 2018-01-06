# Command Line Interface Training

The following training methods are currently implemented in the Command Line Interface


Callsign Receive Practice

Keyboard Interactive Callsign Receive Practice

Random Groups Receive Practice

Wordsworth Receive Practice

Receive / Transmit Echo Practice
 
To enable the command line based training, uncomment this line in your features file:

    #define FEATURE_TRAINING_COMMAND_LINE_INTERFACE

To access the CW training module, in the command line interface execute the \K command and you will see this menu:

    CW Training Menu

    C - Callsign Receive Practice
    I - Keyboard Interactive Callsign Receive Practice
    R - Random Groups Receive Practice
    W - Wordsworth Receive Practice
    E - Receive / Transmit Echo Practice

    X - Exit

## Callsigns

    Callsign Practice Menu

    I - International Callsigns
    U - US Callsigns
    E - European Callsigns
    C - Canadian Callsigns

    X - Exit

## Random Groups

    Random Code Menu

    A - Letter Groups
    1 - Number Groups
    M - Mixed Groups

    X - Exit

## Wordsworth

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


## Receive / Transmit Echo Practice

    Receive / Transmit Echo Practice Menu

    I - International Callsigns
    U - US Callsigns
    E - European Callsigns
    C - Canadian Callsigns
    P - Progressive 5 Character Groups
    2 - Two Letter Words
    3 - Three Letter Words
    4 - Four Letter Words
    N - Names
    Q - QSO Words
    M - Mixed

    X - Exit


In Receive / Transmit Echo Practice, the keyer will send you text and you need to send it back correctly.  If you send correctly, the keyer will beep and send the next text.  If you make a mistake, the keyer will give a boop and resend the text to you.

The Progressive mode will start with one character and each time you send a correct response it will add another character to the string until you reach five characters.

# Command Mode Training

Currently Alphabet sending practice is implemented in Command Mode.  To compile it, uncomment:

#define FEATURE_ALPHABET_SEND_PRACTICE

In Command Mode, send an S to enter Alphabet Send Practice.  You'll hear a beep.  You should then send the alphabet (A, B, C...).  The keyer will send a beep for each correct letter, and a boop for each time you make a mistake.  Press the command mode to exit this mode.