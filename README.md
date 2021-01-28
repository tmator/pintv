#Introduction

PinTV est distribué sour licence GPL.

Vous avez le droit de vendre des mods utilisant PinTV, je vous demande juste de :
- respecter la licence
- laisser la première image de boot
- citer le projet et le lien vers le projet github : https://github.com/tmator/pintv


Enjoy,
Brice.

N'hésiter pas à faire remonter vos avis et vos souhaits.

# Télécharger la dernière version

Nouveautées et explications :
- changement du player (plus rapide)
- vous pouvez modifier la deuxième image affiché au boot en remplacant le fichier splash.png dans /boot (lecteur boot sous windows)
- vous n'avez ensuie qu'a mettre vos vidéos (recommandé 640x480 avi xvid) dans le dossier pintv de la partition share

Vous pouvez trouver la dernière image pour raspi ici : https://drive.google.com/drive/folders/1wsidyBMAH21yRGcpMR4OQpSB_Tw288Xh?usp=sharing

-----------------------------------------------------------------------

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

