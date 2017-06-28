### Arduino Due Hardware

To compile the code for the Arduino Due, uncomment HARDWARE_ARDUINO_DUE in keyer_hardware.h.

The Due does not have EEPROM memory like the other Arduino boards.  So either you must run the code without EEPROM functionality, or install an external EEPROM.  Support for the [E24C1024 EEPROM](http://www.mouser.com/Search/ProductDetail.aspx?R=CAT24C256LI-Gvirtualkey69800000virtualkey698-CAT24C256LI-G) is available; compile in FEATURE_EEPROM_E24C1024.  If you do not install external EEPROM hardware, you cannot compile in FEATURE_MEMORIES and all settings will be volatile (they will not survive a reboot).  You will also notice that the keyer does the beep-boop-beep-boop-beep-boop at power up to indicate that it is initializing with “factory” settings.  This is because there is no EEPROM to pull settings from and the code thinks it is being booted up for the first time.
