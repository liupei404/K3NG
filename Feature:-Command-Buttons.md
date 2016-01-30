# Command Buttons
## Hardware Setup
The command buttons are multiplexed; a series of buttons separated by a resistor each so that they can share a single pin. The software will detect the resistance and determine which button was pushed. You must use the same value of resistor between each button. On the [schematic](https://github.com/k3ng/k3ng_cw_keyer/wiki/Build:-Schematic) these are labeled R8-R12 and are 1k by default. R7 is a resistor with a default value of 10k. If you change the value of either of these resistors you much adjust the software.

## Configuring Software
To enable the command buttons, uncomment this line in keyer_features_and_options.h prior to compiling:

    #define FEATURE_COMMAND_BUTTONS

Button 0 is the command button.  Pressing it will put the keyer into command mode which is described in detail below.  Holding down the command button and pressing the left or right paddles will increase or decrease the CW speed.

Buttons 1 through 12 will play memories when momentarily depressed.  To have a memory autorepeat (such as for doing a repetitive CQ), hold down the memory button and tap the left paddle.  Holding buttons 1 through 6 down for a half second will switch the transmitter (1 through 6), if multiple PTT lines are enabled.

Buttons are multiplexed on one analog line using a voltage divider.  You do not have to install all the buttons, and you can actually configure the number of buttons by changing this compile time setting in keyer_settings.h:

    #define analog_buttons_number_of_buttons 4

Two other settings are used to define the voltage divider resitor values:

    #define analog_buttons_r1 10
    #define analog_buttons_r2 1

analog_buttons_r1 is the value of R7 in the schematic in K (kilo ohms), and analog_buttons_r2 is the value of the remaining resistors (R8, R9, R10, R11, R12, etc.) The code calculates the voltage values for each button at runtime based on the three settings above.  If you decide to use other resistor values you can adjust these values in the code, just be sure to do the math and make sure the resistors you chose make reasonable voltages and currents.