# F.A.Q. #

## When will the 3945 or 2100 be supported? ##

We do not have this card in house. We can write test code, but no release is currently working. We are looking for skilled developers with a 2100 or 3945abg card to help.

## When will configuration via the Airport menu be supported? ##

Most likely never. Its hard to say because we must analyze the IO80211Family which is closed source and not well documented. Use NetworkSelector instead.

## How do I install or upgrade my driver? ##

Please refer to the [installation guide](http://code.google.com/p/iwidarwin/wiki/Installation). Upgrades follow the same procedure as a new installation.

## Where do I get the latest version of the driver? ##

Check the [home page](http://code.google.com/p/iwidarwin/) for download links of the latest versions.

## Why is my card detected as an ethernet adapter instead of an Airport card? ##

This is normal and to be expected. We wrote the driver this way because the IO80211Family is closed source and not well documented. There is more information available for "wired" adapters in Mac OS. The basic networking functions of your card will be handled by the OS, while wireless features are controlled with our NetworkSelector and nsGui utilities.
Both utilities are currently under development and therefore are not expected to be fully operational.

## What is NetworkSelector? ##

NetworkSelector is used to configured the wireless card. Read more [here](http://code.google.com/p/iwidarwin/wiki/NetworkSelector)

## What is nsGui? ##

nsGui is the graphical version of the NetworkSelector utility.  When development is complete, nsGui will be accessed in System Preferences, with an option for it to reside in the menu bar.

## When will WEP or 802.1x be supported? ##

Because of the closed source nature of OSX86 it will be hard to make progress in this area. It may be possible in the future with an improved driver and networkselector application but currently only unencrypted networks are supported

## What driver do I use for my 2915abg? ##

Please install the iwi2200 driver.

## Why is my 2915abg is unable to connect to my unencrypted 802.11a network? ##

We are aware of this issue. Please use 802.11b in the meantime.

## Do I need to update my version of OSX to 10.4.8+ to use this driver? ##

Nope, the iwi driver works with 10.4.4 to 10.4.9 including SSE2 kernels.

## How do I create log's to help development of the drivers? ##

  1. open Terminal
```
  % sudo -s
  % cd ~/Desktop
  % dmesg > dmesg.txt
  % cat /var/log/system.log > system.txt
  % ioreg -w 0 > ioreg.txt
```
  1. Now you have 3 log files; dmesg.txt, system.txt and ioreg.txt you can find them on the desktop

## How can I uninstall the driver? ##

First you must determine which driver is installed, either iwi2100, iwi3945 or iwi2200.
  1. open Terminal
```
  % sudo -s
  % rm -rf /System/Library/Extensions/iwiXXXX.kext (replace XXXX with your specific driver)
  % rm -rf /Library/Receipts/iwiXXXX.pkg
  % rm /System/Library/Extensions.*
  % kextcache -k /System/Library/Extensions
```
  1. Driver is now uninstalled

## Error: Could not get ID for kernel control. 2 ##

This error means one of the following
  * The iwi2200 driver is not installed
  * The driver is installed but you have not rebooted
  * The kext did not load for some reason (are you in safe mode?)

## My WIFI LED does not turn on ##

Right now the wireless LED has no relation to the state of the wireless card. Meaning your card could be on or off, connected or not and the LED will stay in its current state. You can manually turn the LED off and on using NetworkSelector if you wish.

## When I try to connect with NetworkSelector nothing happens ##

Make sure you are not trying to associate with an encrypted network. If you choose an encrypted network from the list you will be retuned to the main menu in a short time and no connection is established.

## -Basic Troubleshooting- ##

Please see [Troubleshooting](http://code.google.com/p/iwidarwin/wiki/Troubleshooting)


## Where to report bugs ##

If can use Google project, send your report to [issues](http://code.google.com/p/iwidarwin/issues/list).
If not please reply to this thread http://forum.insanelymac.com/index.php?showtopic=36976.


### Information to include in bug reports ###

The following information is required in bug reports.

  * Version of iwi. _**important**_
  * iwi message logs (type "grep iwi /var/log/system.log > report.log" and attach "report.log" and dmesg). _**important**_
  * ioreg log
  * Kernel version
  * Mac OS X version
  * IO80211Family version
  * What you were doing when the bug occured

## My question is not answered in this FAQ ##

Please join the discussion over on the InsanelyMac forum by click this link http://forum.insanelymac.com/index.php?showtopic=36976