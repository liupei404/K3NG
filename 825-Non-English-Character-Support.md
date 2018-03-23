### Non-English Characters

To enable support for non-English characters (i.e. À, Ä, È, Ö, etc.), uncomment this line:

    #define OPTION_NON_ENGLISH_EXTENSIONS

If you need to customize the characters for your locality or language, modify the code in functions send_char() and convert_cw_number_to_ascii().  This support was added in version 2012011701 and currently works only with the command line interface and the K1EL Winkey interface protocol emulation.  Support for the PS2 keyboard is in the works.