# Introduction

An SD card is supported through the installation of an SD shield.  The keyer provides basic file system support, somewhat like the classic DOS 8.3 operating system, but with Unix style commands.  Currently some Mill Mode, Beacon, and EEPROM functions are supported in the SD functionality, but more functionality

# Configuration

Enable the SD card functionality with FEATURE_SD_CARD_SUPPORT in your features file.  If your SD card does not use pin 4 for the SPI SS line, change this line in your setting file:

    #define sd_card_spi_ss_line 4

Note that pin 4 is used by default for the sidetone line.  So if you do not change your sidetone pin, every time the SD card is accessed by the keyer, you'll hear clicking in the sidetone speaker.  This does not appear to hurt anything, nor does sidetone on the SD card SPI SS line harm anything either.

# SD Commands


    \:ls <directory>                : List files
    \:cat <filename>                : Print a file
    \:md <directory>                : Make a directory
    \:rm <filename>                 : Delete a file
    \:cp <from_file> <to_file>      : Copy a file
    \:rmdir <directory>             : Delete a directory
    \:saveeeprom <filename>         : Save EEPROM to a file
    \:loadeeprom <filename>         : Load EEPROM from a file
    \:printlog                      : Print Mill log file
    \:clearlog                      : Clear Mill log file

Note that the copy (cp) command requires file path and filenames.  Unlike Unix or DOS equivalents, copying to a directory name isn't supported.  But it can be done like so:

    \:cp /this_dir/filename.txt /that_dir/filename.txt

If you want to move a file, do a cp then an rm on the source file, like this:

    \:cp /this_dir/filename.txt /that_dir/filename.txt
    \:rm /this_dir/filename.txt

# Filesystem Notes

Note that the SD card acts like an old DOS filesystem with 8.3 names like FILENAME.TXT.  File names are case insensitive.  Long filenames are not supported.  Enjoy, kids.  You'll learn what it was like working with files on floppy disks in 1987, except instead of a 1.44 MB limit you have several GB to work with. :-)

The keyer doesn't keep track of a current directory, so no pwd command, no . or .. stuff.  If you want all this you should buy a computer.  ("What's a computer?", she asked.  "Little twit" I thought.  "It's what you plug your iPad into so it can do things.", I replied.  Sigh.)

# Beacon Mode Support

If a text file named beacon.txt is placed in a directory called /keyer/ , the keyer will automatically go into beacon mode at boot up and send the beacon file text continually, until a paddle is hit.