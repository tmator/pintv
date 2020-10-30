# pintv

req :
- https://raspberrypiwiki.com/2.8_inch_Touch_Screen_for_Pi_zero
- raspi zero + sd
- 3d printer

How to :
- Install driver on raspian 
- Install Mplayer

apt-get update
apt-get install mplayer

into pintv.sh :

#!/bin/bash
mplayer -vo fbdev2 -fs -fixed-vo -loop 0 /home/pi/pintv/* &> /dev/null


chmod +x /home/pin/pintv.h

apt-get remove --purge lightdm

wget https://raw.githubusercontent.com/adafruit/Raspberry-Pi-Installer-Scripts/master/read-only-fs.sh
sudo bash read-only-fs.sh

CONTINUE? [y/N] y
Enable boot-time read/write jumper? [y/N] n
Install GPIO-halt utility? [y/N] n
Enable kernel panic watchdog? [y/N] y

Target system type:
1. Pi 3 / Pi Zero W
2. All other models

SELECT 1-2: 1

Boot-time R/W jumper: NO
Install GPIO-halt: NO
Enable watchdog: YES (Pi 3 / Pi Zero W)

CONTINUE? [y/N] y


REBOOT NOW? [y/N] n

add on /boot/cmdline.txt to stop screen blanking

consoleblank=0

add at the end of /home/pi/.bashrc
/home/pi/pinth.sh

//if you nedd to go into rw mode
sudo mount / -o remount,rw
sudo mount /boot -o remount,rw  

