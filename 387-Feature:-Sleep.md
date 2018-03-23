### Sleep Mode

Sleep mode will put the unit to sleep after a certain amount of inactivity, in order to preserve battery power.  To enable the feature, uncomment this line:

    #define FEATURE_SLEEP

The inactivity timer is set here (the unit is minutes):

    #define go_to_sleep_inactivity_time 10

To wake the keyer after it goes to sleep, simply hit the left (normally dit) paddle.