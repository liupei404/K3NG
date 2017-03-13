# Command Mode

To _enter_ command mode, press button 0, the command button and you will hear a “boop beep”. After the beep you can enter various commands by sending character using the paddle.  (Note: if you’re in bug or straight key mode, you will temporarily be switched to iambic in command mode.)

If you enter a bogus command or the keyer didn’t recognize the character you sent, it will send a question mark, upon which you can retry your command.

To _exit_ command mode, send X in CW using the paddles or just press the command button again upon which you will hear “beep boop” and you’ll be back in regular sending mode.

## Available Commands

* A - Switch to Iambic A mode
* B - Switch to Iambic B mode
* D - Switch to Ultimatic mode
* E - Announce the speed in WPM
* F - Adjust sidetone frequency
* G - Switch to bug mode
* I - TX enable / disable
* J - Dah to dit ratio adjust
* N - Toggle paddle reverse
* O - Toggle sidetone on / off
* P# - Program a memory (See options section below)
* S - Alphabet Send Practice
* T - Tune mode
* V - Toggle potentiometer active / inactive
* W - Change speed
* X - Exit command mode (you can also press the command button (button0) to exit)
* Z - Autospace On/Off
* # - Play a memory without transmitting

## Options for P Command

The behavior of the P command (program memory) can be changed with the following compile time options. None of these settings will affect memory programming when using the command line interface (CLI).

Remove all the trailing spaces from memories programmed in command mode with this option:

    #define OPTION_PROG_MEM_TRIM_TRAILING_SPACES

Limit the number of consecutive wordspaces that will be written to a memory with this option:

    #define program_memory_limit_consec_spaces 1