There are several features that can be turned on and options that can be used to enhance your k3ng keyer. Below are the lines. To enable, they must be uncommented by removing the // at the beginning of the line.


| Features | Location | Notes |
| ---- |:----:|:---------------|
|[FEATURE_COMMAND_BUTTONS](https://github.com/k3ng/k3ng_cw_keyer/wiki/Feature:-Command-Buttons) | keyer_features_and_options.h | Enable command buttons 
|FEATURE_COMMAND_LINE_INTERFACE | keyer_features_and_options.h | Enable command line interface over serial connection
|FEATURE_MEMORIES | keyer_features_and_options.h | on the Arduino Due, you must have FEATURE_EEPROM_E24C1024 and E24C1024 EEPROM hardware in order to compile this
|FEATURE_MEMORY_MACROS | keyer_features_and_options.h | 
|FEATURE_WINKEY_EMULATION | keyer_features_and_options.h | 
|FEATURE_BEACON | keyer_features_and_options.h | 
|FEATURE_CALLSIGN_RECEIVE_PRACTICE | keyer_features_and_options.h | 
|FEATURE_POTENTIOMETER | keyer_features_and_options.h | Speed control, if enabled, must have pot connected or false wpm will trigger changes randomly
|FEATURE_SERIAL_HELP  | keyer_features_and_options.h | show help for command line interface
|FEATURE_HELL | keyer_features_and_options.h | 
|FEATURE_PS2_KEYBOARD | keyer_features_and_options.h | Use a PS2 keyboard to send code - Change keyboard layout (non-US) in K3NG_PS2Keyboard.h.  Additional options below.
|FEATURE_USB_KEYBOARD | keyer_features_and_options.h | Use a USB keyboard to send code - Uncomment three lines in k3ng_keyer.ino (search for note_usb_uncomment_lines)
|FEATURE_CW_COMPUTER_KEYBOARD | keyer_features_and_options.h | Have an Arduino Due or Leonardo act as a USB HID (Human Interface Device) keyboard and use the paddle to "type" characters on the computer
|FEATURE_DEAD_OP_WATCHDOG | keyer_features_and_options.h | 
|FEATURE_AUTOSPACE | keyer_features_and_options.h | 
|FEATURE_FARNSWORTH | keyer_features_and_options.h | 
|FEATURE_DL2SBA_BANKSWITCH | keyer_features_and_options.h | Switch memory banks feature as described here: http://dl2sba.com/index.php?option=com_content&view=article&id=131:nanokeyer&catid=15:shack&Itemid=27#english
|FEATURE_LCD_4BIT | keyer_features_and_options.h | classic LCD disidefplay using 4 I/O lines
|FEATURE_LCD_ADAFRUIT_I2C | keyer_features_and_options.h | Adafruit I2C LCD display using MCP23017 at addr 0x20
|FEATURE_LCD_ADAFRUIT_BACKPACK | keyer_features_and_options.h | Adafruit I2C LCD Backup using MCP23008
|FEATURE_LCD_YDv1 | keyer_features_and_options.h | YourDuino I2C LCD display with old LCM 1602 V1 ic
|FEATURE_LCD1602_N07DH | keyer_features_and_options.h | http://linksprite.com/wiki/index.php5?title=16_X_2_LCD_Keypad_Shield_for_Arduino
|FEATURE_CW_DECODER | keyer_features_and_options.h | Decode CW into the keyer
|FEATURE_SLEEP | keyer_features_and_options.h | go to sleep after x minutes to conserve battery power (not compatible with Arduino DUE, may have mixed results with Mega and Mega ADK)
|FEATURE_ROTARY_ENCODER | keyer_features_and_options.h | Use a rotary encoder for speed control
|FEATURE_CMOS_SUPER_KEYER_IAMBIC_B_TIMING | keyer_features_and_options.h | 
|FEATURE_DIT_DAH_BUFFER_CONTROL | keyer_features_and_options.h | 
|FEATURE_HI_PRECISION_LOOP_TIMING | keyer_features_and_options.h | 
|FEATURE_USB_MOUSE | keyer_features_and_options.h | Uncomment three lines in k3ng_keyer.ino (search for note_usb_uncomment_lines)
|FEATURE_CAPACITIVE_PADDLE_PINS | keyer_features_and_options.h | remove the bypass capacitors on the paddle_left and paddle_right lines when using capactive paddles
|FEATURE_LED_RING | keyer_features_and_options.h | Mayhew Labs Led Ring support for rotary encoder
|FEATURE_ALPHABET_SEND_PRACTICE | keyer_features_and_options.h | enables command mode S command - created by Ryan, KC2ZWM
|FEATURE_PTT_INTERLOCK | keyer_features_and_options.h | 
|FEATURE_QLF | keyer_features_and_options.h | 
|FEATURE_EEPROM_E24C1024 | keyer_features_and_options.h | 
|FEATURE_STRAIGHT_KEY | keyer_features_and_options.h | 
|FEATURE_DYNAMIC_DAH_TO_DIT_RATIO | keyer_features_and_options.h | 
|FEATURE_PADDLE_ECHO | keyer_features_and_options.h | 
|FEATURE_STRAIGHT_KEY_ECHO | keyer_features_and_options.h | 
|FEATURE_COMMAND_LINE_INTERFACE_ON_SECONDARY_PORT | keyer_features_and_options.h | Activate the Command Line interface on the secondary serial port
|FEATURE_COMPETITION_COMPRESSION_DETECTION | keyer_features_and_options.h | **Experimental**


| Options | Location | Notes |
| --- |:-------:|:----------------|
|OPTION_PRIMARY_SERIAL_PORT_DEFAULT_WINKEY_EMULATION |keyer_features_and_options.h | Use when activating both FEATURE_WINKEY_EMULATION and FEATURE_COMMAND_LINE_INTERFACE 
|OPTION_SUPPRESS_SERIAL_BOOT_MSG | keyer_features_and_options.h | 
|OPTION_INCLUDE_PTT_TAIL_FOR_MANUAL_SENDING | keyer_features_and_options.h | 
|OPTION_EXCLUDE_PTT_HANG_TIME_FOR_MANUAL_SENDING | keyer_features_and_options.h | 
|OPTION_WINKEY_DISCARD_BYTES_AT_STARTUP | keyer_features_and_options.h | if ASR is not disabled, you may need this to discard errant serial port bytes at startup
|OPTION_WINKEY_STRICT_EEPROM_WRITES_MAY_WEAR_OUT_EEPROM | keyer_features_and_options.h | 
|OPTION_WINKEY_SEND_WORDSPACE_AT_END_OF_BUFFER | keyer_features_and_options.h | 
|OPTION_WINKEY_STRICT_HOST_OPEN | keyer_features_and_options.h | require an admin host open Winkey command before doing any other commands
|OPTION_WINKEY_2_SUPPORT | keyer_features_and_options.h | comment out to revert to Winkey version 1 emulation
|OPTION_WINKEY_EXTENDED_COMMANDS | keyer_features_and_options.h | **in development**
|OPTION_WINKEY_SEND_BREAKIN_STATUS_BYTE | keyer_features_and_options.h | additional code to check_dit_paddle() and check_dah_paddle() to send 0xC2 status byte when paddles are hit
|OPTION_WINKEY_INTERRUPTS_MEMORY_REPEAT | keyer_features_and_options.h | 
|OPTION_WINKEY_2_HOST_CLOSE_NO_SERIAL_PORT_RESET | keyer_features_and_options.h | activate this when using Winkey 2 emulation and Win-Test
|OPTION_WINKEY_FREQUENT_STATUS_REPORT | keyer_features_and_options.h | activate this to make Winkey emulation play better with RUMlog and RUMped
|OPTION_WINKEY_IGNORE_LOWERCASE | keyer_features_and_options.h | Enable for typical K1EL Winkeyer behavior (use for SkookumLogger version 1.10.14 and prior to workaround "r" bug)
|OPTION_REVERSE_BUTTON_ORDER | keyer_features_and_options.h | This is mainly for the DJ0MY NanoKeyer http://nanokeyer.wordpress.com/
|OPTION_PROG_MEM_TRIM_TRAILING_SPACES | keyer_features_and_options.h | trim trailing spaces from memory when programming in command mode
|OPTION_DIT_PADDLE_NO_SEND_ON_MEM_RPT | keyer_features_and_options.h | this makes dit paddle memory interruption a little smoother
|OPTION_MORE_DISPLAY_MSGS | keyer_features_and_options.h | additional optional display messages - comment out to save memory
|OPTION_N1MM_WINKEY_TAB_BUG_WORKAROUND | keyer_features_and_options.h | enable this to ignore the TAB key in the Send CW window (this breaks SO2R functionality in N1MM)
|OPTION_WATCHDOG_TIMER | keyer_features_and_options.h | this enables a four second ATmega48/88/168/328 watchdog timer; use for unattended/remote operation only
|OPTION_MOUSE_MOVEMENT_PADDLE | keyer_features_and_options.h | **experimental** (just fooling around) - mouse movement will act like a paddle
|OPTION_NON_ENGLISH_EXTENSIONS | keyer_features_and_options.h | add support for additional CW characters (i.e. À, Å, Þ, etc.)
|OPTION_KEEP_PTT_KEYED_WHEN_CHARS_BUFFERED | keyer_features_and_options.h | this option keeps PTT high if there are characters buffered from the keyboard, the serial interface, or Winkey
|OPTION_DISPLAY_NON_ENGLISH_EXTENSIONS | keyer_features_and_options.h | LCD display suport for non-English (NO/DK/DE) characters - Courtesy of OZ1JHM
|OPTION_UNKNOWN_CHARACTER_ERROR_TONE | keyer_features_and_options.h | Play a tone when an unknown character is entered, aka you messed up so bad the keyer hasn't a clue :-)
|OPTION_DO_NOT_SAY_HI | keyer_features_and_options.h | 
|OPTION_USE_ORIGINAL_VERSION_2_1_PS2KEYBOARD_LIB | keyer_features_and_options.h | 
|OPTION_PS2_NON_ENGLISH_CHAR_LCD_DISPLAY_SUPPORT | keyer_features_and_options.h | makes some non-English characters from the PS2 keyboard display correctly in the LCD display (donated by Marcin sp5iou)
|OPTION_PS2_KEYBOARD_RESET | keyer_features_and_options.h | reset the PS2 keyboard upon startup with 0xFF (contributed by Bill, W9BEL)
|OPTION_SAVE_MEMORY_NANOKEYER | keyer_features_and_options.h | 
|OPTION_CW_KEYBOARD_CAPSLOCK_BEEP
|OPTION_CW_KEYBOARD_ITALIAN | keyer_features_and_options.h | 
|OPTION_CW_DECODER_GOERTZEL_AUDIO_DETECTOR
|OPTION_INVERT_PADDLE_PIN_LOGIC | keyer_features_and_options.h | 
|OPTION_ADVANCED_SPEED_DISPLAY | keyer_features_and_options.h | enables "nerd" speed visualization on display: wpm, cpm (char per min), duration of dit and dah in milliseconds and ratio (contributed by Giorgio, IZ2XBZ)
|OPTION_DIT_DAH_BUFFERS_OFF_BY_DEFAULT _FOR_FEATURE_DIT_DAH_BUFFER_CONTROL | keyer_features_and_options.h | 
|OPTION_PROSIGN_SUPPORT | keyer_features_and_options.h | additional prosign support for paddle and straight key echo on display, CLI, and in memory storage
|OPTION_RUSSIAN_LANGUAGE_SEND_CLI | keyer_features_and_options.h | Russian language CLI sending support (contributed by Павел Бирюков, UA1AQC)