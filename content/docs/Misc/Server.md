# Server

My little server is called "Kantica" - it means "little bucket". Below is an in-progress knowledgebase for running and mantaining it.



## TODO

Get css working on local nginx server  

call ISP to see if my port 80 is blocked and try to ask nicely to unblock it

![Kantica screenfetch snip](/favicon.PNG)

This nice looking preview is from [Screenfetch](https://github.com/KittyKatt/screenFetch), a favourite of the linux ricing community.

Use SSH to access the server

```
ssh kantica@srce.duckdns.org -p 4241
```

the RSA private key that is used to authenticate this is located in C:\Users\Rafael\\.ssh



## The very basics

Shutdown

```
sudo poweroff
```

Reboot

```
sudo reboot
```

Who would have thunk?

## Packages

Packages are found [Here](https://packages.ubuntu.com/). 

Packages are manipulated with **A**dvanced **P**ackage **T**ool, the main CLI package manager for Debian and its derivatives.  

Install using this command

```
sudo apt install [package name]
```

They are removed using this command

```
sudo apt remove [package name]
```

Occasionally, update all packages using this command 

```
sudo apt-get update && sudo apt-get dist-upgrade
```

get update downloads the latest list of packages and their versions, while dist-upgrade updates (fucking language, right?) all outdated packages intelligently,

## Backups

Backups are done locally, using [Timeshift](https://github.com/teejee2008/timeshift). 

Use this to make a new snapshot

```
sudo timeshift --create
```

Use this to list all snapshots

```
sudo timeshift --list
```

Use this to restore a snapshot

```
timeshift --restore --snapshot "2020-02-19_18-32-36"
```

##   

## Realtime data

The server's performance data is collected using [Netdata](https://github.com/netdata/netdata).  

The data can be viewed on the local network on the address [IP:1999](http://192.168.5.20:19999).

Temperature integration is WIP, so currently check temps with

```
sudo watch sensors
```

Netdata can also send notifications for various critical states. Setting this up is WIP, currently being blocked by setting up a web domain on the server. Since sendmail can't send emails from an internal server, it needs to connect to a webserver, something about setting A dns records, which I can't easily do as my website is being held hostage.

## Sleep 

A sleep function for the server is WIP. It should wake the server up whenever there is a hit on the webpage, [like described here](https://ubuntuforums.org/showthread.php?t=2045541).    

Update: This seems to require a router with OpenWrt firmware. Since I do not have that, the next line of inquiry would be setting up an arduino or teensy to act as a listener and wake up the server once traffic is recieved on the URL.  

Another possibility is setting up the router to

## Startup  

Related to the sleep function, this is a simple way of checking how long the last boot up took.

```
systemd-analyze
```

This shows which processes take up what amount of boot time.

```
 systemd-analyze blame
```

This disables a process

```
sudo systemctl disable NetworkManager-wait-online.service
```

While this reverts the change

```
sudo systemctl enable NetworkManager-wait-online.service
```

Be reaaaaaaaaly careful with this.