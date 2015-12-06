# Introduction #
This is currently installation documents for iwi2200.
updated fro v6(or v0.6).

## Support Hardware ##
  * Intel Pro/wireless 2200BG/2945ABG

## Requirement ##
  * Mac OS X 10.4.7 or later.

# Steps #
Steps 2-3 are typed into Terminal

  1. go to Terminal.App
  1. extract file
> > type in terminal
> > zip version
```
% unzip -l iwi2200.zip 
```
> > tgz version
```
% tar zxvf iwi2220.tgz 
```
  1. change owner
```
% sudo chown -R root:wheel iwi2200.kext
```
> > If you are asked for a password, enter your password.
  1. load kernel module
```
  % sudo kextload iwi2200
```
  1. enabling power
> > press airpot power button?
> > ( I dont know detail , my machine cannot set power button)


> if power is enable, "Radio is disable" display.

> edit file iwi2200/Contents/Info.plist and change value 1 to 0
```
                        <key>p_disable</key>
                        <integer>1</integer> 
```
```
                        <key>p_disable</key>
                        <integer>0</integer> <- should change
```
> > and reboot. after reboot, plz load kernel modeul ( 3.)
  1. in 10.4.8
> > if you dont work, you can set "use\_10\_4\_8" options
```
                        <key>use_10_4_8</key>
                        <integer>0</integer> 
```
```
                        <key>p_disable</key>
                        <integer>1</integer> <- should change
```

## about setup ##
  * cannot sepcified network name via Airport menu. only automatic association.
  * if you cat get ip address after enable from airport menu , it work ( but nothing is displayed in airport menu).
  * availably operation in airport menu  is ip address setting and enabling. if another is set , it will not change anything.

## Warning ##
  * this driver only work in open network .
  * this driver cannot specified network name. only automatic detection.
  * if u cannot get IP address via dhcp, you set static IP address.
  * if large file try to send and recieve , it may fail.


## Bugs ##
about bug report

if can use google project, send report to [issues](http://code.google.com/p/iwidarwin/issues/list).
if not, send report to http://forum.insanelymac.com/index.php?showtopic=36976.
but i may forget report in forums.

_we recommend to send report to http://code.google.com/p/iwidarwin/issues/list_

u must test with **debugging version**.
if normal version, driver dont output sevaral information.

### Bug report ###
The following information is required in bug reports.

  * Version of iwi
  * Kernel version
  * Mac OS X version
  * IO80211Family version
  * Procedure of occuring bug.
  * iwi message log( /var/log/system.log and dmesg ( if overflow in dmesg, type "grep iwi /var/log/system.log > report.log" and attached "report.log").

if information is lacking , I dont know where is problem.

## About 10.4.8 ##
  * Crashed in 10.4.8  when  you set channel in Airpot menu.
> > if open network and dont use encrpytion , it worked.

  * cannot start network scanning and associating!
> > if you display " Failed to send TX\_POWER: Already sending a command." in log.


> it may work in "use\_10\_4\_8" options

## Log message ##
  * iwi2200 part of /var/log/system.log  or dmesg ( if overflow logs, system.log)
  * ioreg (not must )

## Options ##
there are following driver options.

### p\_mode ###
this is set station mode.
  * p\_mode=1
> > station is ad-hoc mode.
  * p\_mode=0
> > this is defaults. this is infrastructure mode( this is the mode to connect to AP).

### p\_led ###
this is enabling of LED.
you can set 0 or 1.

### p\_disable ###
this is enabling automaticaly enabling of wireless power.
  * p\_disable=1
> > wireless adaptor is not enable automaticaly so must enabling airport interface.
  * p\_disable=0
> > wireless adapotr is enable automatically in loading modules.
> > this should be set in Mac OS X> 10.4.8.



# Caution #
We dont never answer about following question .
and it reduce our motivation. plz understand it.

  * when 3945abg work ?
  * "**" function support in future version?
  * when new version release?**
