# Command Line Interface Training

The following training methods are currently implemented in the Command Line Interface


Receive Practice

Keyboard Interactive Receive Practice

Random Groups Receive Practice

Wordsworth Receive Practice

Receive / Transmit Echo Practice
 
To enable the command line based training, uncomment this line in your features file:

    #define FEATURE_TRAINING_COMMAND_LINE_INTERFACE

To access the CW training module, in the command line interface execute the \K command and you will see this menu:

    CW Training Menu

    C - Receive Practice
    I - Keyboard Interactive Receive Practice
    R - Random Groups Receive Practice
    W - Wordsworth Receive Practice
    E - Receive / Transmit Echo Practice

    X - Exit

Receive Practice sends code without any interruption.  The Keyboard Interactive Receive Practice sends code that then waits for you to enter using the CLI keyboard what was sent.  Random Groups Receive Practice sends various letter and number five character groups.  Wordsworth is described in more detail below.

## Receive and Keyboard Interactive Receive Practice



    Menu

    I - International Callsigns
    U - US Callsigns
    E - European Callsigns
    C - Canadian Callsigns
    2 - Two Letter Words
    3 - Three Letter Words
    4 - Four Letter Words
    N - Names
    Q - QSO Words
    M - Mixed Words   

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

## Alphabet Send Practice 

Command: S

Compilation: #define FEATURE_ALPHABET_SEND_PRACTICE

Upon entering Alphabet Send Practice mode you will hear a beep.  You should then send the alphabet (A, B, C...).  The keyer will send a beep for each correct letter, and a boop for each time you make a mistake.  Press the command mode to exit this mode.

## Send / Receive Echo Practice - Progressive Five Character Groups

Command: U

Compilation: #define FEATURE_COMMAND_MODE_PROGRESSIVE_5_CHAR_ECHO_PRACTICE

Upon entering this mode the keyer will send ECHO in CW.  The Progressive mode will start with one character and each time you send a correct response it will add another character to the string until you reach five characters.  If you make a mistake, the keyer will repeat the current CW string.  Press the command mode to exit this mode.