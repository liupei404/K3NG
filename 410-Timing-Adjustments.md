
### Autospace

The autospace feature can be toggled on and off with the Z command in command mode, the \z command in the command line interface, and CTRL-Z using the PS2 keyboard.  This feature “cleans up” manual sending a bit by automatically inserting a wordspace delay if the operator waits more than one dit after sending a dit or dah to paddle either paddle.  The autospace feature is activated by uncommenting this line:

    #define FEATURE_AUTOSPACE

### Wordspace Adjustment

Wordspace is the key up time in between words.  By default it is set for seven dit lengths by this line in keyer_settings.h:

    #define default_length_wordspace 7

This can be adjusted using the \y command line interface command.

### Keying Compensation

The keying compensation filter extends the time of both dits and dahs to compensate for older transmitters that are slow on the draw in QSK at higher speeds.  The inter-element key up times are reduced a corresponding amount of time.  The time in mS can be set here in keyer_settings.h:

    #define default_keying_compensation 0

Currently there is no command to adjust this at runtime, however the Winkey emulation will adjust this if it is set in the host application.

### First Element Extension Time

This feature makes the first dit or dah sent longer to compensate for slow T/R switches in rigs.  The time is set here in keyer_settings.h:

    #define default_first_extension_time 0

Currently there is no command to adjust this at runtime, however the Winkey emulation will adjust this if it is set in the host application.
