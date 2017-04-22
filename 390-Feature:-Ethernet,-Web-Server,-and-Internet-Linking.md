_This section is under construction_

The K3NG Keyer has code for supporting Ethernet shields and provides a web server and Internet linking capability.

# Web Server

The web server is activated by enabling FEATURE_WEB_SERVER in your features and options file.  Settings for the Ethernet interface are located in your settings file.

    #if defined(FEATURE_ETHERNET)
      // #define FEATURE_ETHERNET_IP {192,168,1,178}                      // default IP address ("192.168.1.178")
      // #define FEATURE_ETHERNET_MAC {0xDE,0xAD,0xBE,0xEF,0xFE,0xED}
      #define FEATURE_ETHERNET_IP {192,168,1,179}                      // default IP address ("192.168.1.179")
      #define FEATURE_ETHERNET_MAC {0xDE,0xAD,0xBE,0xEF,0xFE,0xEE}

      #define FEATURE_ETHERNET_GATEWAY {192,168,1,1}                   // default gateway
      #define FEATURE_ETHERNET_SUBNET_MASK {255,255,255,0}                  // default subnet mask
      #define FEATURE_ETHERNET_WEB_LISTENER_PORT 80
      #define FEATURE_UDP_SEND_BUFFER_SIZE 128
      #define FEATURE_UDP_RECEIVE_BUFFER_SIZE 128
    #endif //FEATURE_ETHERNET

The configuration included in the settings file shows how to setup two units.  Naturally, each needs to have a unique IP address (FEATURE_ETHERNET_IP) and MAC address (FEATURE_ETHERNET_MAC).  The gateway (FEATURE_ETHERNET_GATEWAY) is typical set to the gateway address of the LAN, and in home networks the subnet mask (FEATURE_ETHERNET_SUBNET_MASK) is typical 255.255.255.0.  FEATURE_ETHERNET_WEB_LISTENER_PORT specifies the TCP port the webserver will listen on, with port 80 being the default port for web services.

Note that the network settings in the settings file are used on boot up and written to EEPROM settings the first time the code is run.  If the network settings are changed using the Network Setting page (shown below), the settings in EEPROM are updated.  (If you make a mistake with the network settings using the Network Settings web page, you can recover the network settings by changing eeprom_magic_number in the .ino file and uploading the code.  The new magic number will tell the code to reinitialize the EEPROM with fresh settings.)

## Operation

To access the web server, enter the IP address of the Arduino Ethernet shield for the address, for example:

http://192.168.1.179/

## The Main Main Web Page

![image](https://cloud.githubusercontent.com/assets/3332720/25308903/5cc5389e-278d-11e7-834b-7b93d8439a44.png)


## Control Page

![image](https://cloud.githubusercontent.com/assets/3332720/25308935/f0bd059a-278d-11e7-9b8d-4d7e2e7de0c0.png)

The Control page has several variations:

    /ctrl - Regular Control Page

    /ctrlnd - Control Page, No Display

    /ctrlnd?st<TEXTTOSEND>/ - Send CW text for example: 
                              http://192.168.1.179/ctrlnd?sttest/ will sent TEST in CW

## Memories Page

![image](https://cloud.githubusercontent.com/assets/3332720/25308940/023fc410-278e-11e7-9512-c98fd8045cbe.png)

## Keyer Settings Page

![image](https://cloud.githubusercontent.com/assets/3332720/25308945/19002f5a-278e-11e7-85e5-f738cc670124.png)

## Network Settings

![image](https://cloud.githubusercontent.com/assets/3332720/25308953/3ba9b3f0-278e-11e7-97e6-526363714fee.png)    

# Internet Linking

The Internet Link functionality allows you to link two keyers together, with one sending keying data to the other.  Any keying on the sending keyer will be mimicked on the receiving keyer, including paddle, straight key, CLI, Winkeyer, and keyboard sending.  The Internet linking uses a simple UDP protocol that compensates for latency and jitter over the Internet in order to provide the most accurately timed keying.  Note that there may be a slight delay between the keying on the sending keyer and the keying on the receiving keyer, however the keying timing (which is most important) should be preserved. 

Internet linking is activated using FEATURE_INTERNET_LINK.  This feature has FEATURE_WEB_SERVER as a dependency.

Note that if you are sending link data across the Internet and you're behind firewall on either or both ends, you will need to configure NAT (Network Address Translation).  Configuration of NAT is beyond the scope of this Wiki page.  Google is your friend.

## Link Setup Example

Sending Side

![image](https://cloud.githubusercontent.com/assets/3332720/25308913/9554f19a-278d-11e7-8b6c-87e38bae3946.png)

Receiving Side

![image](https://cloud.githubusercontent.com/assets/3332720/25308923/bb717ea2-278d-11e7-9747-478daeef1f2e.png)





