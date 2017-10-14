# Get more trackers

See no peers for some torrent(s)? Add more tracker(s) from Transmission

## Installation
* Download script and make it executable:

```
wget --no-check-certificate -O /opt/bin/add_trackers.sh https://raw.githubusercontent.com/AndrewMarchukov/tracker-add/master/tracker-add.sh
chmod +x /opt/bin/add_trackers.sh
```
or

```
wget --no-check-certificate -O /opt/bin/add-trackers-auto.sh https://raw.githubusercontent.com/AndrewMarchukov/tracker-add/master/tracker_add_auto.sh
wget --no-check-certificate -O /etc/systemd/system/transmission-tracker-add.service https://raw.githubusercontent.com/AndrewMarchukov/tracker-add/master/transmission-tracker-add.service
chmod +x /opt/bin/add_trackers_auto.sh
systemctl daemon-reload
```
## Usage
Automatically checks new torrents and adds trackers
```
systemctl enable transmission-tracker-add.service
systemctl start transmission-tracker-add.service

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
Run manual script to add some more trackers for active torrents:

```
/opt/bin # ./add_trackers.sh
Processing torrent #77...
Adding trackers for torrent name...
* http://www.opentrackr.org/announce... failed.
* http://mgtracker.org:2710/announce... failed.
Processing torrent #94...
adding trackers for torrent name...
* http://www.opentrackr.org/announce... done.
* http://tracker.bittorrent.am/announce... done.
* http://retracker.krs-ix.ru:80/announce... done.
* http://mgtracker.org:2710/announce... done.
* http://explodie.org:6969/announce... done.
```

Don't be confused with `failed` message. In most cases, it means tracker(s) already added and/or exists in current torrent.
