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

To access the web server, enter the IP address of the Arduino Ethernet shield for the address, for example:

http://192.168.1.179/


The Control page has several variations:

    /ctrl - Regular Control Page

    /ctrlnd - Control Page, No Display

    /ctrlnd?st<TEXTTOSEND>/ - Send CW text for example: http://192.168.1.179/ctrlnd?sttest/ will sent TEST in CW

    

# Internet Linking

Internet linking is activated using FEATURE_INTERNET_LINK.  This feature has FEATURE_WEB_SERVER as a dependency.





