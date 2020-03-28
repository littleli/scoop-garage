# MPD

MPD stand for Music Player Daemon. It's a flexible, powerful, server-side application for playing music. Through plugins and libraries it can play a variety of sound files while being controlled by its network protocol.

## Installation

```sh
scoop install mpd
```

## Setup

MPD requires a config file

This is how a minimum configuration file `mpd.conf` may look like:

```conf
music_directory	"c:/music"
playlist_directory "c:/mpd/playlists"
db_file	"c:/mpd/database"
log_file	"c:/mpd/log"

input {
	plugin "curl"
}

audio_output {
	type		"winmm"
	name		"WinMM output"
}
```

You have to adjust directories to your existing setup. Important recommendations:

* `playlist_directory` is really a directory, it has to exist in the target location

Unfortunatley this may not be enough. Especially if you Windows audio setup is more complex and you have multiple audio devices and driver. In such case please it's going to be more demanding to setup. Please take a look at [mpd.conf](mpd.conf). All above properties should have some configuration values.
