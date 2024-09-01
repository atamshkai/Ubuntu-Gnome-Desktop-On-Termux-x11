# Ubuntu-Gnome-Desktop-On-Termux-x11

This is a preinstalled Ubuntu Distro with Gnome Desktop.For Android 12 & 13,before you install it , disable phantom process killer. 

[Here](https://github.com/atamshkai/Phantom-Process-Killer/tree/main) 

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
tar -xvJf zsh.tar.xz && mv ~/zsh/.* ~/
rm -rf ~/zsh
chsh -s zsh 
``` 

#### Then, Add Sound 

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
### Warning

If you upgrade the system,the desktop will fail to launch.

#### Fix it

```
for file in $(find /usr -type f -iname "*login1*"); do 
mv -v $file "$file.back"
done
```
```
echo "chmod u+s /usr/lib/dbus-1.0/dbus-daemon-launch-helper" >>~/.bashrc
```
```
mv -v /usr/share/applications/gnome-sound-panel.desktop /usr/share/applications/gnome-sound-panel.desktop.back
```
```
echo "export XDG_CURRENT_DESKTOP=GNOME" >>~/.bashrc
```

Login again 
```
exit
```

## Termux 
[Download](https://github.com/termux/termux-app/releases/tag/v0.118.1) 

## Termux-x11 
[Download](https://github.com/termux/termux-x11/releases/tag/nightly) 

## Termux-x11 Custom Resolution
1920:1080
