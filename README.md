# Get more trackers

See no peers for some torrent(s)? Add more tracker(s) from Transmission

## Installation
* Download script and make it executable:

```
wget --no-check-certificate -O /opt/bin/add_trackers.sh https://raw.githubusercontent.com/AndrewMarchukov/tracker-add/master/tracker-add.sh
chmod +x /opt/bin/add_trackers.sh
```

## Usage

Run script to add some more trackers for active torrents:

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
