## Code Compilation

All of the features will not fit on an Arduino Uno simultaneously.  If the compiled code goes over about 28.5K, the upload a stock Uno will fail.  The Nano holds slightly more than a stock Arduino.

You can burn an alternate bootloader to your Uno called [Optiboot](http://code.google.com/p/optiboot/) which will free up an additional 1.5K of program space to stuff additional features on to your Uno.

The [Arduino Mega](http://arduino.cc/en/Main/ArduinoBoardMega) will run the entire “nine yards” compiled and is a fun board.  The Arduino Due will also run all of the code.
