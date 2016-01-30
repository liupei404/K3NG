# Configuring the Keyer Code

Starting with (stable release) Version 2.0, the configuration options and various other settings are broken out into separate files. You will mostly be working with key_feature_and_options.h until you start deciding to use different pins than the schematics plan for or modify the way the keyer works.

> **[keyer_features_and_options.h](https://github.com/k3ng/k3ng_cw_keyer/blob/master/keyer_features_and_options.h)**: configure the features you want here. A list of features, options and their descriptions can be found in the [Features and Options](https://github.com/k3ng/k3ng_cw_keyer/wiki/Features-and-Options) page.

> **[keyer_pin_settings.h](https://github.com/k3ng/k3ng_cw_keyer/blob/master/keyer_pin_settings.h)**: map the pins you’re using with your hardware

> **[keyer_settings.h](https://github.com/k3ng/k3ng_cw_keyer/blob/master/keyer_settings.h)**: various settings for features; you probably won’t need to touch this unless you’re a power user or want to tweak stuff

> **[keyer_debug.h](https://github.com/k3ng/k3ng_cw_keyer/blob/master/keyer_debug.h)**: turns on debugging code; you probably won’t ever have to touch this unless you’re deep in the code or someone on the Radio Artisan group asks you to enable debugging and post the debug logs for troubleshooting purposes

> **[keyer.h](https://github.com/k3ng/k3ng_cw_keyer/blob/master/keyer.h)**: this is for some IDEs like [Sublime/Stino](https://github.com/Robot-Will/Stino) that require function prototypes in order to compile (or don’t fully auto-generate function prototypes at compile time); leave the include in the main .ino file commented out unless you need this (if you don’t know if you need this, you don’t need it) _UPDATE:_ Stino versions after October 2014 no longer require this file.  Yeahhhh!

> **[k3ng_keyer.ino](https://github.com/k3ng/k3ng_cw_keyer/blob/master/k3ng_keyer.ino)**: this is the main code; object declarations for some hardware devices are included in this file

> **[keyer_hardware.h](https://github.com/k3ng/k3ng_cw_keyer/blob/master/keyer_hardware.h)**: This is for defining custom or preset configurations.  More detail elsewhere in this wiki.

> **[keyer_dependencies.h](https://github.com/k3ng/k3ng_cw_keyer/blob/master/keyer_dependencies.h)**: Don’t touch this file.  [You’ll shoot your eye out.](https://www.youtube.com/watch?v=mrAwb9ptu9U)

This may look complicated and daunting at first, however the instructions in this wiki go into detail on what to configure at compile time in order to get the features you want, so don’t fear.  It is recommended to start with a minimal software and hardware feature set, then add additional features as needed or if you just want to play around. Be patient and you’ll be rewarded with a darn fun and useful keyer.
