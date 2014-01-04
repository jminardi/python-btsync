python-btsync
=============

The BTSync class found in btsync.py is a light wrapper around the Bittorrent Sync API.
For now, this code assumes a btsync instance is running with a working API key.
(see the **Notes** section for more info on how to get this set up.)

Installation
------------
_If you haven't already, you need to 
[download the Bittorrent Sync Application](http://www.bittorrent.com/sync/downloads)_

```bash
$ git clone https://github.com/jminardi/python-btsync.git
$ cd python-btsync
$ python setup.py install
```

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

Notes
-----

To use the API you will need to apply for a key. You can find out
how to do that, and learn more about the btsync API here:

<http://www.bittorrent.com/sync/developers/>
        
Once you receive your key, you need to enter it into the config file.
See `config.json` for a sample config file.

Then quit BTSync if it is running, and start it from the command line with the --config flag:

`/Applications/BitTorrent\ Sync.app/Contents/MacOS/BitTorrent\ Sync --config path/to/config.json`
