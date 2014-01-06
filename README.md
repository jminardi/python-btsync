python-btsync
=============

The BTSync class found in `btsync.py` is a light wrapper around the Bittorrent Sync API.
For now, this code assumes a btsync instance is running with a working API key.
(see the **Notes** section for more info on how to get this set up.)

Installation
------------
```bash
$ git clone https://github.com/jminardi/python-btsync.git
$ cd python-btsync
$ python setup.py install
```
_You will also need a recent version of the [Bittorrent Sync Application][0]_
[0]: http://www.bittorrent.com/sync/downloads


Basic Use
---------

```python
>>> # this code assumes a btsync instance is running
>>> from btsync import BTSync
>>> btsync = BTSync()
>>> btsync.get_folders()
[{u'dir': u'/Users/jack/sync/notes',
  u'error': 0,
  u'files': 13,
  u'indexing': 0,
  u'secret': u'NOPE',
  u'size': 70867,
  u'type': u'read_write'}]
```

Implemented Methods
-------------------
At this time, not all API calls are implemented.

* [x] Get folders
* [x] Add folder
* [x] Remove folder
* [x] Get files
* [ ] Set file preferences
* [ ] Get folder peers
* [x] Get secrets
* [ ] Get folder preferences
* [ ] Set folder preferences
* [ ] Get folder hosts
* [ ] Set folder hosts
* [ ] Get preferences
* [ ] Set preferences
* [ ] Get OS name
* [ ] Get version
* [ ] Get speed
* [ ] Shutdown


Notes
-----

To use the API you will need to apply for a key. You can find out
how to do that, and learn more about the btsync API here:

<http://www.bittorrent.com/sync/developers/>
        
Once you receive your key, you need to enter it into the config file.
See `config.json` for a sample config file.

Then quit BTSync if it is running, and start it from the command line with the --config flag:

`/Applications/BitTorrent\ Sync.app/Contents/MacOS/BitTorrent\ Sync --config path/to/config.json`
