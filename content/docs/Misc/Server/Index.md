# Server

My little server is called "Kantica" - it means "little bucket". Below is an in-progress knowledgebase for running and mantaining it.

![Kantica screenfetch snip](img/kantica.PNG)

This nice looking preview is from [Screenfetch](https://github.com/KittyKatt/screenFetch), a favourite of the linux ricing community.

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

