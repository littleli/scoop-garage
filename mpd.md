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
log_file "c:/mpd/log"

input {
	plugin "curl"
}

audio_output {
	type "winmm"
	name "WinMM output"
}
```

You have to adjust directories to your existing setup. Important recommendations:

* `playlist_directory` is really a directory, it has to exist in the target location

Unfortunatley this may not be enough. Especially if you Windows audio setup is more complex and you have multiple audio devices and driver. In such case please it's going to be more demanding to setup. Please take a look at [mpd.conf](mpd.conf). All above properties should have some configuration values.

## MPD as a Windows Service

Having terminal opened just for the sake of havin mpd.exe running is annoying. There is a solution to this as well. Here's the example command that you have to run as Administrator to wrap the binary as a Windows service:

```sh
 sc.exe create mpd binPath= "C:\Users\youruser\scoop\shims\mpd.exe D:\mpd\mpd.conf"
```

Of course, you have to adjust path to your mpd.exe shim and also path to your mpd configuration file. Once you do that you have nice access to services facilities. You can now do following self-explanatory commands:

```sh
sc.exe start mpd
sc.exe stop mpd
```

And also `mpd` is now acceessible through Task Manager tab "Services".
