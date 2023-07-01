# Ubuntu-Gnome-Desktop-On-Termux-x11

This is a preinstalled Ubuntu Distro with Gnome Desktop.For Android 12 & 13,before you install it , disable phantom process killer. 

[Watch Video Here](https://youtu.be/UxmQSETvAOc) 

## Preview 

![](https://raw.githubusercontent.com/atamshkai/Ubuntu-Gnome-Desktop-On-Termux-x11/main/jelly.png) 

# To Do 

#### First,Download Ubuntu Distro From Here.
[Download](https://archive.org/download/ubuntu.tar.xz/ubuntu.tar.xz) 

## Installation 

Download ubuntu.tar.xz to Device's Download folder first. 

### Install zsh 

``` 
pkg up -y && pkg i -y zsh wget 
wget https://github.com/atamshkai/Termux-Zsh/raw/main/zsh.tar.xz
tar -xvJf zsh.tar.xz && mv zsh/.* ~/ && rm -rf zsh && chsh -s zsh 
``` 

#### Then, 

``` 
echo "killall pulseaudio &>/dev/null" >>~/.zshrc 
``` 
``` 
echo "pulseaudio --start --exit-idle-time=-1; pacmd load-module module-native-protocol-tcp auth-ip-acl=127.0.0.1 auth-anonymous=1" >>~/.zshrc 
``` 
``` 
pkg up -y && pkg i -y x11-repo && pkg i -y proot-distro pulseaudio termux-x11-nightly 
``` 
``` 
termux-setup-storage 
``` 
``` 
proot-distro restore /sdcard/download/ubuntu.tar.xz 
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
proot-distro login ubuntu --shared-tmp 
```
#### I forgot to install pulseaudio for sound.So install it.
```
apt update && apt install -y pulseaudio
```
#### Then 
``` 
export DISPLAY=:1
export PULSE_SERVER=127.0.0.1
export XDG_CURRENT_DESKTOP=GNOME
service dbus start
gnome-shell --x11
```
OR 
```
gnome 
``` 

## Termux 

[Download](https://github.com/termux/termux-app/releases/download/v0.118.0/termux-app_v0.118.0+github-debug_universal.apk) 

## Termux-x11 

[Download](https://archive.org/download/termux-x11/app-universal-debug.apk)
