python-btsync
=============

The `BTSync` class is a light wrapper around the [Bittorrent Sync API][1].
For now, this code assumes a btsync instance is running with a working API key.
(See the **Notes** section for more info on how to get this set up.)

[1]: http://www.bittorrent.com/sync/developers/api

Installation
------------

Installation under windows:
Installation of BTSync under windows is a bit finnicky and without error messages, so this simplifies it.

Install BTSync in a regular directory , not something like "Program files" which needs admin access. 
Exit from BTSync if it's running 
Go to the BTSync directory , delete everything except BTSync.exe
Edit the api key in windows_config.json
Run BTSync.exe /config path_to_windows_config_json
If all goes well BTSync will launch.

After cloning pyhon-btsync:
Set line 10 in python-btsync./btsync.py with the executable directory

If you want to change admin/password/port , you'll have to repeat this process after changing admin/password/port both in windows_config.json and in python_btsync/btsync.py 


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
At this time, not all API calls are implemented. However, you can still 
make any API call manually using the `request()` method like so:

```python
btsync.request({'method': 'get_folder_peers', 'secret': '<yoursecret>'})
```

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

```bash
$ /Applications/BitTorrent\ Sync.app/Contents/MacOS/BitTorrent\ Sync --config path/to/config.json
```
