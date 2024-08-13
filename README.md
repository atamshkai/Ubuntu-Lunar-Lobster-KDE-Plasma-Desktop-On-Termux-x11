# Ubuntu-Lunar-Lobster-KDE-Plasma-Desktop-On-Termux-x11

This is a preinstalled Ubuntu-Linux Distro with KDE Plasma Desktop.For Android 12 & 13,before you install it,disable phantom process killer. 

[Here](https://github.com/atamshkai/Phantom-Process-Killer/tree/main)

## Preview ![](https://raw.githubusercontent.com/atamshkai/Ubuntu-Lunar-Lobster-KDE-Plasma-Desktop-On-Termux-x11/main/ubuntu-lunar-kde.png) 

# To Do 

#### First,Download Lunar-KDE Distro From Here. 
[Download](https://archive.org/download/lunar-kde/lunar-kde.tar.xz
) 

## Installation 
Download lunar-kde.tar.xz to Device's Download folder first. 

### Install zsh 
``` 
pkg up -y && pkg i -y zsh wget
wget https://github.com/atamshkai/Termux-Zsh/raw/main/zsh.tar.xz 
tar -xvJf zsh.tar.xz && mv ~/zsh/.* ~/
rm -rf ~/zsh
chsh -s zsh 
``` 
#### For Sound, 
``` 
echo "killall pulseaudio &>/dev/null" >>~/.zshrc 
``` 
```
echo "pulseaudio --start --exit-idle-time=-1; pacmd load-module module-native-protocol-tcp auth-ip-acl=127.0.0.1 auth-anonymous=1" >>~/.zshrc 
```
#### Install needed packages 
``` 
pkg up -y && pkg i -y x11-repo && pkg i -y proot-distro pulseaudio termux-x11-nightly 
``` 
#### Give Storage Permission

``` 
termux-setup-storage 
```
### Add lunar-kde to proot-distro
```
echo "DISTRO_NAME='Lunar Lobster  (lunar-lobster)'" >>~/../usr/etc/proot-distro/lunar-kde.sh
```
### Restore Lunar Lobster KDE Distro
```
proot-distro restore /sdcard/download/lunar-kde.tar.xz 
``` 
``` 
exit 
``` 
#### Login again to terminal 
Before login to proot,start termux-x11 first. 
``` 
termux-x11 :1 
``` 
#### Then,open another session & login 
``` 
echo "proot-distro login lunar-kde --shared-tmp --bind /dev/null:/proc/sys/kernal/cap_last_cap" >>~/../usr/bin/lunar-kde
```
```
chmod +x ~/../usr/bin/lunar-kde
```
#### Start Lunar Lobster KDE Plasma Desktop
```
lunar-kde
```
#### Then 
``` 
rm /run/dbus/pid
dbus-daemon --system
sleep 4
export PULSE_SERVER=127.0.0.1
env DISPLAY=:1 dbus-launch startplasma-x11 -dpi 120
``` 
OR 
``` 
kde 
``` 
## Termux 
[Download](https://github.com/termux/termux-app/releases/download/v0.118.0/termux-app_v0.118.0+github-debug_universal.apk) 
## Termux-x11 
[Download](https://archive.org/download/termux-x11/app-universal-debug.apk) 
## Termux-x11 Custom Resolution
1920:1080
