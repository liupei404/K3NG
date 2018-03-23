### Multiple Serial Ports

Some Arduino models like the Mega have multiple serial ports.  With this keyer code it is possible to run two serial ports simultaneously.  One port can run Winkey emulation, the other can run the Command Line Interface, or both can run the CLI.

To use this feature, enable FEATURE_COMMAND_LINE_INTERFACE_ON_SECONDARY_PORT in keyer_features_and_options.h.

This enables a Command Line Interface on a secondary serial port of your choosing, defined in keyer_settings.h:

    #define SECONDARY_SERIAL_PORT &Serial1
    #define SECONDARY_SERIAL_PORT_BAUD 115200

If you enable FEATURE_WINKEY_EMULATION and OPTION_PRIMARY_SERIAL_PORT_DEFAULT_WINKEY_EMULATION, the primary serial port will go into Winkey emulation mode at boot up. The primary serial port is also defined in keyer_settings.h:

    #define PRIMARY_SERIAL_PORT &Serial

If you hold down the command button at boot up, the primary serial port will switch to Command Line Interface mode.

To summarize some configuration combinations:

> FEATURE_COMMAND_LINE_INTERFACE (only) – CLI on the primary port (“Serial0”)
>
> FEATURE_WINKEY_EMULATION (only) – Winkey on the primary port (“Serial0”)
>
> FEATURE_COMMAND_LINE_INTERFACE+FEATURE_WINKEY_EMULATION+ OPTION_PRIMARY_SERIAL_PORT_DEFAULT_WINKEY_EMULATION: Winkey on the primary port (“Serial0”) by default, hold command button at boot up for CLI
>
> FEATURE_COMMAND_LINE_INTERFACE+FEATURE_WINKEY_EMULATION: CLI on the primary port (“Serial0”) by default, hold command button at boot up for Winkey
>
> FEATURE_COMMAND_LINE_INTERFACE+FEATURE_WINKEY_EMULATION+ OPTION_PRIMARY_SERIAL_PORT_DEFAULT_WINKEY_EMULATION+FEATURE_COMMAND_LINE_INTERFACE_ON_SECONDARY_PORT: Winkey on the primary port (“Serial0”) by default, hold command button at boot up for CLI on primary port (“Serial0”), CLI on secondary port (Serial1) all the time
> 
> FEATURE_COMMAND_LINE_INTERFACE+FEATURE_COMMAND_LINE_INTERFACE_ON_SECONDARY_PORT: CLI on both primary port (“Serial0”) and secondary port (Serial1) all the time
