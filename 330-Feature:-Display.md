# LCD Display

This keyer supports an LCD display, either the standard commonplace Hitachi LCD display in four bit mode, the [Adafruit LCD I2C RGB shield](http://adafruit.com/products/714) & [I2C Character Backpack](https://www.adafruit.com/product/292), the [YourDuino I2C LCD display](http://arduino-info.wikispaces.com/LCD-Blue-I2C), and the [Linksprite 16 X 2 LCD Keypad Shield](http://linksprite.com/wiki/index.php5?title=16_X_2_LCD_Keypad_Shield_for_Arduino).

To configure the LCD display, follow these steps:

_First_, Uncomment only one of the lines below in features files (typically keyer_features_and_options.h).  The appropriate line will depend on your display type:

    #define FEATURE_LCD_4BIT                // classic LCD display using 4 I/O lines
    #define FEATURE_LCD_ADAFRUIT_I2C          // Adafruit I2C LCD display using MCP23017 at addr 0x20
    #define FEATURE_LCD_ADAFRUIT_BACKPACK    // Adafruit I2C LCD Backup using MCP23008 (courtesy Josiah Ritchie, KE0BLL)
    #define FEATURE_LCD_YDv1                // YourDuino I2C LCD display with old LCM 1602 V1 ic
    #define FEATURE_LCD1602_N07DH      // http://linksprite.com/wiki/index.php5?title=16_X_2_LCD_Keypad_Shield_for_Arduino
    #define FEATURE_LCD_SAINSMART_I2C
    #define FEATURE_LCD_FABO_PCF8574

_Second_, If you are using the 4 bit LCD display, setup the I/O pins you want to use:

    #define lcd_rs A2
    #define lcd_enable 10
    #define lcd_d4 6
    #define lcd_d5 7
    #define lcd_d6 8
    #define lcd_d7 9

Note that the Adafruit I2C displays use pins A4 and A5 by default for interfacing as these are the hardware I2C pins.  No pin setup is required in the code when using this dispay.

No pin setup is required when using FEATURE_LCD1602_N07DH

_Third_, If you are using a display that does not used the default 16 columns and 2 rows, adjust these two lines in the keyer_settings.h file.

    #define LCD_COLUMNS 16
    #define LCD_ROWS 4

_Fourth_, If you have free memory, uncomment this line for more messages on the display:

    #define OPTION_MORE_DISPLAY_MSGS

At higher CW speeds, the sending speed may be impacted by I2C LCD displays.  This can be rectified by
increasing the I2C bus speed in file twi.h (it will be in ….\arduino-1.0.1\libraries\Wire\utility). Alter this line:

    #define TWI_FREQ 100000L

…and change the setting to something like 500000L.  (Thanks to AD7KG for discovering this bug and testing the fix.)

To change the character that is used to indicate unknown characters in paddle echo, customize this line:

    #define unknown_cw_character ‘*’

(If you want to hear a sound when an unknown character is sent, enable OPTION_UNKNOWN_CHARACTER_ERROR_TONE)
