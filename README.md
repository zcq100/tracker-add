# Get more trackers

See no peers for some torrent(s)? Add more tracker(s) from Transmission

## Installation
* Download script and make it executable:
Edit settings for transmission set rpc-enabled, rpc-username and rpc-password
```
wget --no-check-certificate -O /opt/bin/add-trackers-auto.sh https://raw.githubusercontent.com/AndrewMarchukov/tracker-add/master/tracker_add_auto.sh
wget --no-check-certificate -O /etc/systemd/system/transmission-tracker-add.service https://raw.githubusercontent.com/AndrewMarchukov/tracker-add/master/transmission-tracker-add.service
chmod +x /opt/bin/add_trackers_auto.sh
Set user and password in add_trackers_auto.sh
systemctl daemon-reload
```
## Usage
Automatically checks new torrents and adds trackers:
```
systemctl enable transmission-tracker-add.service
systemctl start transmission-tracker-add.service

service transmission-tracker-add status
● transmission-tracker-add.service - transmission tracker add
   Loaded: loaded (/etc/systemd/system/transmission-tracker-add.service; enabled; vendor preset: enabled)
   Active: active (running) since; 0 days ago
 Main PID: 19102 (add_trackers_au)
   CGroup: /system.slice/transmission-tracker-add.service
           ├─19102 /bin/bash /opt/bin/add-trackers-auto.sh
           └─31204 sleep 5
           
```




## Extra manual script
Set user and password in add_trackers.sh

Run manual script to add some more trackers for active torrents:

```
/opt/bin # ./add_trackers.sh
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
