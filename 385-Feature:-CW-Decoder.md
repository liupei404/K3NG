### CW Decoder

The keyer can be configured to decode off the air CW using FEATURE_CW_DECODER.  The decoded character are displayed in both the Command Line Interface (CLI) and LCD display, whichever is configured.  The input pin for the CW decoder is defined in keyer_pin_settings.h:

    #define cw_decoder_pin A11

If you wish to have a indicator to assist in tuning in the CW signal and setting levels, define this output pin:

    #define cw_decoder_indicator 24

This is especially useful with the DSP Audio Decoder described below, driving an LED indicator.

The CW decoder can be interfaced two ways:

### External Tone Decoder Hardware

If external tone decoding hardware is used, cw_decoder_pin is a straight digital input.  Drive it low (0V) when there is a CW signal, and high (+5V) when there is no CW tone.

### DSP Audio Tone Decoder

To activate the audio tone decoder in software, activate OPTION_CW_DECODER_GOERTZEL_AUDIO_DETECTOR. This option compiles in a [Goertzel DSP](http://en.wikipedia.org/wiki/Goertzel_algorithm) audio detector.  The code used in the CW keyer was originally written by Hjalmar skovholm Hansen, OZ1JHM  and is described further on [his project web page](http://www.skovholm.com/cwdecoder).  When using this option cw_decoder_pin must be an analog pin, such as A1, A2, A3, etc.

The DSP audio tone decoder requires two library files: [goertzel.h](https://github.com/k3ng/k3ng_cw_keyer/blob/master/libraries/goertzel.h) and [goertzel.cpp](https://github.com/k3ng/k3ng_cw_keyer/blob/master/libraries/goertzel.cpp).  Goertzel.h contains several settings:

    #define GOERTZ_SAMPLING_FREQ 8928.0
    #define GOERTZ_NOISE_BLANKER_INITIAL_MS 6
    #define GOERTZ_TARGET_FREQ 558.0
    #define GOERTZ_SAMPLES 64

    #define GOERTZ_MAGNITUDE_LIMIT_LOW 100
    #define GOERTZ_MAGNITUDE_THRESHOLD 0.6
    #define GOERTZ_MOVING_AVERAGE_FILTER 6

Prior to making changes, please read the notes in the source code.  The sampling frequency is CPU dependent and there is a mathematical relationship between the sampling frequency, target frequency, and number of samples.

The Arduino Due has an 84 Mhz clock, so the sampling frequency will be different than the Arduino Uno and Mega which both have a 16 Mhz clock.  For the Due, you can use these settings:

    #define GOERTZ_SAMPLING_FREQ 46872.0
    #define GOERTZ_SAMPLES 168

To interface the audio with the Arduino, consult [Hjalmar’s project page](http://www.skovholm.com/cwdecoder) for the circuit.  It’s very simple.  A 10k ohm resistor goes from +5V to the analog pin, and a 10k ohm resistor is placed from the analog pin to ground.  This biases the analog pin at +2.5 volts.  The audio is coupled to the analog pin via a 0.1 uF capacitor.

As far as tuning in signals, I have found that the DSP decoders better when receiver filters are wide.  It’s counterintuitive, but narrow CW filters seem to make the DSP decoding not perform as well.  Also, the optimal audio level appears to be just slightly above the threshold where tone detection occurs.  An LED using the cw_decoder_indicator output pin is very helpful in determining this point.

The CW decoder is still a bit experimental and it is planned to improve the decoding algorithm.
