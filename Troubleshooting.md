Before testing anything lets cover the basics. Did you run the installer iwi2200.pkg? Have you rebooted after installation? Can you verify the kext is loaded with the command `kextstat | grep iwi` from a terminal?

1) Make sure the card is listed in Network Preferences for your current location. Unplug any other network connections you might have (ethernet, usb). iwi's driver won't work properly if you're connected to multiple networks.

2) Run the [NetworkSelector](http://code.google.com/p/iwidarwin/wiki/NetworkSelector) utility and verify the card is turned on. Wait a few moments and use option 0 to refresh the screen and verify the card is still shown as powered

3) Make sure you are within range of an unencrypted 802.11b network and use option 2 "network list" to see if the unencrypted network is listed. The network will have a number next to it and if you type that number [NetworkSelector](http://code.google.com/p/iwidarwin/wiki/NetworkSelector) will try to connect. Wait a few moments and use option 0 to refresh and the network should now be listed as associated at the top of [NetworkSelector](http://code.google.com/p/iwidarwin/wiki/NetworkSelector).

4a) Open a terminal window and run the command `ifconfig` and verify if an IP address has been assigned.
  * If you get a message "adapter not present" make note of the MAC address listed in Network Preferences and then run "ifconfig" and find the matching MAC and interface name
  * If you see " media: autoselect (<unknown type>) status: inactive " or " media: autoselect (none) status: inactive " Then the card is either powered off or an unencrypted network was not detected.
  * If you see "media: autoselect status: active" but no IP address is listed then DHCP messages aren't being received

**Or**

4b) Open "System preferences" and choose "Network." Under the "Show" choose "Network Status."
  * If the message is "Built-in Ethernet = The cable for Built-in Ethernet is not plugged in" then the card is either powered down or an unencrypted network was not detected.
  * If the message is "Built-in Ethernet = The able for Built-in Ethernet is connected, but your computer does not have an IP address and cannot connect to the internet" then DHCP is not working properly

5) If [NetworkSelector](http://code.google.com/p/iwidarwin/wiki/NetworkSelector) says you are associated with a network and step 4 shows no IP address try setting your address/subnet manually from within "NetworkPreferences"

6) From the terminal try to ping your default gateway. For example `ping 192.168.0.1` (realize the gateway could be any number and you have to find this yourself). Press Ctrl-C to stop the ping.

7) If you can ping the gateway you should then try to ping an internet host `ping 67.17.144.1`

8) Last try `ping google.com` and wait a few seconds to verify DNS is working.