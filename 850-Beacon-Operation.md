# Memory Based Beacon

Enabling FEATURE_BEACON and grounding left paddle at boot up will cause the keyer to go into beacon mode and repeat memory 1 continually.

# SD Card Based Beacon

A beacon can also be implemented using an SD card shield.  Enable FEATURE_SD_CARD_SUPPORT and on the SD card create a directory in the root directory called keyer.  Place a text file called beacon.txt with your intended beacon text.  This file will be sent in CW continuously at boot up.  A paddle or button tap will stop the beacon sending.