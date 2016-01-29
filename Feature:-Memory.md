# Memory Operation and Memory Macros

## Operation
Memories can be manually played using buttons 1 through 5, or using the \# command in the command line interface (for example, \1 plays memory 1).  In command mode the memories can be sent without transmitting by entering the number of the memory.

Memories are programmed using the command line interface \p# command or in command mode using the P command.

To program memory 1 with CQ CQ CQ DE K3NG, the command would be \p1CQ CQ CQ DE K3NG.

To program memory 1 using command mode, enter command mode by pressing the command button and sending the P command.  After hearing a beep, send the CW code to be stored and when finished, hit the command button to exit programming.  The keyer will then play back the memory.  If the keyer didn’t recognize a character you sent it will send a question mark in its place.

## Macros

Macros can be placed in memories to do cool things. Some macros include:

    \#       Jump to memory # (1 through 9)
    \c       Play serial number with cut numbers
    \d###    Delay for ### seconds
    \e       Play serial number, then increment
    \f####   Set sidetone to #### hertz
    \h       Switch to Hell sending
    \i#      Insert memory # (This is different from \#, the jump macro.  The insert memory macro plays another memory, then comes back to the memory the keyer was originally playing.  The jump command jumps to the other memory and doesn't come back.)
    \l       Switch to CW (from Hell mode)
    \n       Decrement serial number, do not send
    \q##     Switch to QRSS mode, dit length ## seconds
    \s       Insert space
    \r       Switch to regular speed mode
    \t###    Transmit for ### seconds
    \u       Activate PTT
    \v       Deactivate PTT
    \w###    Set regular mode speed to ### WPM
    \x#      Switch to transmitter # (1, 2, 3, 4, 5, or 6)
    \y#      Increase speed # WPM
    \z#      Decrease speed # WPM
    \+       Prosign the next two characters

(Note that both command line commands and CW memories are case insensitive.)

## Software Configuration

The number of memories is set at compile time using these lines in keyer_settings.hs:

    #define number_of_memories 12
    #define memory_area_start 20
    #define memory_area_end 1023

Up to 12 memories can be configured, with some caveats.  Nine memories are supported in the CLI and in memory macros, and the full 12 are supported with the PS2 keyboard.

Memory_area_start and memory_area_end define the starting and ending EEPROM locations for the entire bank of memory.  The memory area is divided up evenly between the memories.  The example settings above will result in 12 memories each with 83 bytes, or 83 characters.