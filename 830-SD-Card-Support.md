# Introduction

An SD card is supported through the installation of an SD shield.  The keyer provides basic file system support, somewhat like the classic DOS 8.3 operating system, but with Unix style commands.  Currently some Mill Mode, Beacon, and EEPROM functions are supported in the SD functionality, but more functionality

# Configuration

Enable the SD card functionality with FEATURE_SD_CARD_SUPPORT in your features file.  If your SD card does not use pin 4 for the SPI SS line, change this line in your setting file:

    #define sd_card_spi_ss_line 4

Note that pin 4 is used by default for the sidetone line.  So if you do not change your sidetone pin, every time the SD card is accessed by the keyer, you'll hear clicking in the sidetone speaker.  This does not appear to hurt anything, nor does sidetone on the SD card SPI SS line harm anything either.

# SD Commands


    \:ls <directory>                : List files on SD card
    \:cat <filename>                : Print file on SD card
    \:md <directory>                : Make directory on SD card
    \:rm <filename>                 : Delete file on SD card
    \:rmdir <directory>             : Delete directory on SD card
    \:saveeeprom <filename>         : Save EEPROM to SD card
    \:loadeeprom <filename>         : Load EEPROM from SD card
    \:printlog                      : Print Mill log on SD card
    \:clearlog                      : Clear Mill log on SD card

# Filesystem Notes

Note that the SD card acts like an old DOS filesystem with 8.3 names like FILENAME.TXT.  File names are case insensitive.  Currently long filenames are not supported.

# Beacon Mode Support

If a text file named beacon.txt is placed in a directory called /keyer/ , the keyer will automatically go into beacon mode at boot up and send the beacon file text continually, until a paddle is hit.