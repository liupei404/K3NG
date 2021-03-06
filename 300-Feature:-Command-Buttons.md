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

## Warning

Do not enable FEATURE_BUTTONS unless you have the corresponding resistors on the button pin connected.  If the analog button pin does not have +5 volts on it, the keyer will not start up as it thinks there is a button depression in progress.

## Alternate Hardware

### DFRobot LCD Display Buttons

DFRobot LCD display buttons can be used be activating the following option in your features file:

    #define OPTION_DFROBOT_LCD_COMMAND_BUTTONS

Button mappings and analog reading settings are in your settings file:

    // For V1.1 board use these values
    #define dfrobot_btnRIGHT_analog 50
    #define dfrobot_btnUP_analog 250
    #define dfrobot_btnDOWN_analog 450
    #define dfrobot_btnLEFT_analog 650
    #define dfrobot_btnSELECT_analog 850  
    
    // For V1.0 board use these values
    // #define dfrobot_btnRIGHT_analog 50
    // #define dfrobot_btnUP_analog 195
    // #define dfrobot_btnDOWN_analog 380
    // #define dfrobot_btnLEFT_analog 555
    // #define dfrobot_btnSELECT_analog 790  
  
    // button to memory mappings (0 = command button, 1 = memory 1, 2 = memory 2, etc.)
    #define dfrobot_btnRIGHT  2
    #define dfrobot_btnUP     1
    #define dfrobot_btnDOWN   3
    #define dfrobot_btnLEFT   4
    #define dfrobot_btnSELECT 0
    #define dfrobot_btnNONE   255 // do not change

### Command Mode Active LED

If you would like to have an LED activate when in command mode, define this pin and have it power an LED:

    #define command_mode_active_led 0