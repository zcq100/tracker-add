# Get more trackers
See no peers,seeds for some torrent(s)? Add more tracker(s) for Transmission

This script automatically checks new torrents and adds trackers

## Installation and usage

* Docker way

Take image `docker pull andrewmhub/transmission-tracker-add`

```docker run --net=host -d -e HOSTPORT=localhost:9091 -e TR_AUTH=user:password --name=transmission-tracker-add andrewmhub/transmission-tracker-add:latest```

if you need to use another torrent tracker list then use docker run env 

`-e TORRENTLIST=https://raw.githubusercontent.com/user/trackerslist/master/mylist.txt`

you use transmission daemon in docker then read [Docker Documentation](https://docs.docker.com/network/)

* Systemd way

Download script and make it executable:

Edit settings for transmission set rpc-enabled, rpc-username and rpc-password

```
wget --no-check-certificate -O /opt/bin/add-trackers-auto.sh https://raw.githubusercontent.com/AndrewMarchukov/tracker-add/master/tracker-add-auto.sh
wget --no-check-certificate -O /etc/systemd/system/transmission-tracker-add.service https://raw.githubusercontent.com/AndrewMarchukov/tracker-add/master/transmission-tracker-add.service
chmod +x /opt/bin/add-trackers-auto.sh
```
Set user and password in add-trackers-auto.sh
```
systemctl daemon-reload
systemctl enable transmission-tracker-add.service
systemctl start transmission-tracker-add.service

systemctl status transmission-tracker-add.service
● transmission-tracker-add.service - transmission tracker add
   Loaded: loaded (/etc/systemd/system/transmission-tracker-add.service; enabled; vendor preset: enabled)
   Active: active (running) since; 0 days ago
 Main PID: 19102 (add_trackers_au)
   CGroup: /system.slice/transmission-tracker-add.service
           ├─19102 /bin/bash /opt/bin/add-trackers-auto.sh
           └─31204 sleep 5
           
```

* Simple way (for routers)

Requirements: curl, transmission-remote

Download script and make it executable:

Edit settings for transmission set rpc-enabled, rpc-username and rpc-password

```
wget --no-check-certificate -O tracker-add-auto-router.sh https://raw.githubusercontent.com/AndrewMarchukov/tracker-add/master/tracker-add-auto-router.sh
chmod +x tracker-add-auto-router.sh
```
Set user and password in tracker-add-auto-router.sh
```
tracker-add-auto-router.sh &
```





## Extra manual script if you need
Set user and password in manual-tracker-add.sh

Run manual script to add some more trackers for active torrents:

```
/opt/bin # ./manual-tracker-add.sh
URL for https://hastebin.com/raw/bererufibu
Adding trackers for Film.HDRip.AVC.mkv...

######################################################################## 100,0%
* http://tracker.dutchtracking.nl:80/announce... failed.
* http://tracker.edoardocolombo.eu:6969/announce... failed.
* http://tracker.ex.ua:80/announce... failed.
* http://tracker.kicks-ass.net:80/announce... failed.
* http://tracker.mg64.net:6881/announce... done.
* http://tracker.tfile.me/announce... failed.
* http://tracker1.wasabii.com.tw:6969/announce... done.
* http://tracker2.itzmx.com:6961/announce... done.
```

Don't be confused with `failed` message. In most cases, it means tracker(s) already added and/or exists in current torrent.
