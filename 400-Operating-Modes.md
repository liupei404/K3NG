### Beacon Mode

In order to have the keyer go directly into beacon mode at power up or reset and stay in beacon mode, simply ground pin 2.  This is useful for keyers that are dedicated to beacon or fox service.

### Iambic Modes

To switch to Iambic A mode, use the A command in command mode or \a in the command line interface.

To switch to Iambic B mode, use the B command in command mode or \b in the command line interface.

(An explanation of Iambic A and B can be found [here](http://wb9kzy.com/modeab.pdf).)

### Straight Key Support

There are two ways to use a straight key with the keyer:

Go into straight key mode by holding down the right paddle when powering up or power resetting.  This places the keyer exclusively in straight key mode with very limited functionality.
Activate FEATURE_STRAIGHT_KEY in features_and_options.h and define pin_straight_key in keyer_pin_settings.h .  Grounding the pin with a straight key will give you straight key operation in parallel with paddle operation and still give you access to the all the normal keyer functionality.  (The straight key does not work in command mode, however it can be used to program memories when used with FEATURE_STRAIGHT_KEY. )

### Bug Mode

To go into bug mode, use the command mode G command or the command line \g command.

### Ultimatic Mode

To go into Ultimatic mode, use the command mode D command or the command line \d command.

### CMOS Super Keyer Timing

This is enabled by uncommenting this line in keyer_features_and_options.h:

    #define FEATURE_CMOS_SUPER_KEYER_IAMBIC_B_TIMING

And the default timing setting can be set in keyer_settings.h:

    #define default_cmos_super_keyer_iambic_b_timing_percent 33

CMOS Super Keyer Timing applies only to Iambic B mode.  Setting the timing percent to 0 (zero) is essentially pure Iambic B and 100 is pure Iambic A.  This function can be turned on and off at runtime using the command line interface \& command, and the timing percentage can be set using the \% command.  Settings for this are stored in nonvolatile memory.
