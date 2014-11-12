showrss
=======

Fetch new torrents for a specific ShowRSS user and kick-off a download.

Installation
------------

Run the following command:

    $( curl https://raw.github.com/jbmorley/get/master/get-min | python - -P -s '{ "showrss": "git@github.com:jbmorley/showrss.git" }' )

This will use [get](https://github.com/jbmorley/get) to install 'showrss' and add it to your path.

Requirements
------------

Install the requirements:

    $ pip install -r requirements.txt --use-mirrors

### Running under virtualenv

If you do not wish to install your requirements globally, you can create a virtualenv for running showrss. This can be done as follows:

From the folder:

    $ virtualenv --no-site-packages showrss-venv

To get into the virtualenv, source the activate script:

    $ source ./showrss-venv/bin/activate
    
Install the requirements into the venv (see requirements.txt below):

    $ pip install -r requirements.txt --use-mirrors

Run the thing:

    $ python showrss.py

Configuration
-------------

`showrss` expects to find a configuration file at `~/.showrss`:

```ini
[default]

user_id = 12345
command = transmission-remote -a
notifier = /usr/bin/terminal-notifier -title ShowRSS -message
quality = default
```

The configuration file defines two things:

### user_id

Your ShowRSS user identifier.

You can find this by clicking on the 'feeds' link and generating a personal feed. The URL for the feed will be something like:

    http://showrss.info/rss.php?user_id=12345&hd=null&proper=null

Your user_id is the value after `user_id=`. `12345` in this example.

### command

The command-line for starting torrents. The torrent URL is appended to the end of the command.

Transmission on Linux:

```ini
command = transmission-remote -a
```

Transmission on OS X:

```ini
command = open /Applications/Transmission.app
```

### quality (optional)

The desired show quality. May be one of:

- `default` - ShowRSS per-show settings
- `standard` - Only standard torrents
- `high` - Only 720p HD torrents
- `all` - Both types of torrents

### notifier (optional)

The command-line for providing notifications of torrent downloads. The notification message is passed as the last argument.

For example, notifications can be posted to the Notification Center on OS X by using `terminal-notifier`:

```ini
notifier = /usr/bin/terminal-notifier -title ShowRSS -message
```

Changelog
---------

Version 1.0.0, June 2014

- Initial release.

License
-------

showrss is available under the MIT license. See the LICENSE file for more info.