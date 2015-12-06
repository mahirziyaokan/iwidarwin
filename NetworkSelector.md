## Description ##

NetworkSelector controls all wireless aspects of your card. It can -

  * Turn the card on or off if you do not have an external switch.
  * Display the network you are associated with currently.
  * Display any unencrypted networks in the area.
  * Choose which network to associate with if there are many available
  * Change the state of the wireless LED (if equiped).
  * Switch to Ad-Hoc or monitor mode.

## Caution ##

Each version of NetworkSelector is matched to the IWI driver it was included with. Mismatched versions will not function properly.

## Where to get it ##
NetworkSelector should be included in the DMG file of the driver you are installing along with the package file.

## Main Screen ##
```

Wellcome to the insanelyMac SpacePort 0.1
Adapter [mode: 0 led: off]
Associated: 'linksys (00:06:25:10:18:11)' 

1) Turn card off
2) Network List 
3) Switch led 
4) Change mode
5) Close Program 
0) Refresh

Enter Option:  
```

## Description of each option ##
### Adapter [mode: 0 led: off] ###
For information on "mode: 0" look below at "4) Change mode"

For information on "led: off" look below at "3) Switch led"

### Associated: 'linksys (00:06:25:10:18:11)' ###
This line only appears when you are connected to a network. It shows the SSID of the network and the MAC address of the AP you are connected to.

### 1) Turn card off ###
This line will change depending on the state of your card.

### 2) Network List ###
Display detected networks and choose which you would like to associate with by typing the number next to it. Choose 0 to skip association and return to the main screen.
```
hello world: send network list
[1] 'linksys (00:0c:41:d4:40:fb) ch:1' 
[2] 'default (00:0d:72:55:19:d9) ch:6' 
[3] 'netgear (00:06:25:10:b7:97) ch:9'
[4] '2wire123 (00:09:5b:9e:66:24) ch:11'  
select network or type 0 to return
```


### 3) Switch led ###
Turn the wireless LED on your computer on or off

### 4) Change mode ###
Configure the wireless card for either Ad-Hoc(mode 1), Monitor (mode 2) or the default Infrastructure (mode 0).

### 5) Close Program ###
Ill let you guess what this option does

### 0) Refresh ###
Update the display to show current SSID/Mode/Power/LED status

### Note ###
Options (3), (4) only work when the card is powered off

