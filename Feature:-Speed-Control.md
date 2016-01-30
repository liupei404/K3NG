# CW Speed Adjustment

The CW sending speed can be adjusted several ways:

* The W command in command mode
* The command line interface \w command
* The memory macro \w, or \y and \z for incremental increases or decreases
* Holding down the command button (button 0) and pressing the left and right paddles
* Potentiometer Speed Control
* Rotary Encoder Speed Control

## Potentiometer Speed Control

Adjusting the speed pot will immediately change the CW speed during manual sending or memory playing, however its changes will not be written to non-volatile memory.  If the speed is changed using other methods (command mode, command line interface, memory macro, command button shortcut) that will override the pot setting until the pot is adjusted again.

The potentiometer functionality is enabled by commenting out this line in keyer_features_and_options.h:

    #define FEATURE_POTENTIOMETER

The pin the potentiometer wiper is connected to is defined in this line in keyer_pin_settings.h:

    #define potentiometer A0

Only enable this functionality if you have a potentiometer connnected, otherwise stray voltage on the Arduino pin will cause erratic and unexpected speed changes.

## Rotary Encoder Speed Control

Speed can also be controlled using an inexpensive rotary encoder.  The functionality is enabled by uncommenting this line in keyer_features_and_options.h:

    #define FEATURE_ROTARY_ENCODER

The pins for connecting the encoder are defined in these lines in keyer_pin_settings.h:

    #define rotary_pin1 0 // CW Encoder Pin
    #define rotary_pin2 0 // CCW Encoder Pin

The center pin of the rotary encoder should be connected to ground.

### Mayhew Labs LED Ring

To use the [Mayhew Labs Rotary Encode LED Ring](http://mayhewlabs.com/products/rotary-encoder-led-ring) with the rotary encoder speed functionality, uncomment this feature line:

    #define FEATURE_LED_RING

…and define pins here:

    #define led_ring_sdi 0 //Data
    #define led_ring_clk 0 //Clock
    #define led_ring_le 0 //Latch

You can adjust the behavior of the LEDs with these settings:

    #define led_ring_low_limit 10
    #define led_ring_high_limit 50
