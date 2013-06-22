---
layout: page
title: Extensions
show-sidebar: true
group: download
sidebar-group: download
order: 3
---

Banshee is written to be easily enhanced by extensions.  In fact, the Play Queue, Podcasting, and Last.fm support are all extensions.  You can turn extensions on and off within the _Extensions_ tab of the _Preferences_ dialog (under the Edit menu).

Many extensions are included in Banshee itself.  Others are developed and packaged as part of the Banshee Community Extensions project.  And anybody can build and distribute their own 3rd party extension.

### Banshee Community Extensions

#### About

The following extensions are developed mostly by third-parties, and are not vetted by the core Banshee developers (though that will probably change over time).
    
  * **Alarm Clock** - You can use Banshee to wake up or go to sleep to a selection of your own music.
  * **Album Art Writer** - Writes Album Art from cache to the folder containing the music files.
  * **Ampache** - Browse and play your remote music with Ampache.
  * **AppIndicator** - Use the new application indicator area available in Ubuntu.
  * **Awn** - Sets the current album cover as banshee icon in awn.
  * **ClutterFlow** - A CoverFlow clone that allows you to browse your album collection.
  * **Cover Wallpaper** - Sets the current playing album cover as the GNOME desktop wallpaper.
  * **FolderSync** - Copy and synchronize music files from playlists into user-specified folders.
  * **Jamendo** - Download and listen to over 20,000 free albums.
  * **Karaoke** - Filter the singers voice out of songs.
  * **Lastfm Fingerprint** - Identify your music automatically, using the Last.fm online service.
  * **LCD** - Display track info on a LCD using LCDproc.
  * **Lirc** - Control Banshee via a normal (infrared) remote control.  Requires LIRC.
  * **Live Radio** - Another way to discover internet radio stations.
  * **Lyrics** - Fetches and displays lyrics for the current song.
  * **Magnatune** - Listen to streamed music from Magnatune.com.
  * **Mirage** - Adds playback shuffle-by-similar and Auto DJ fill-by-similar modes, based on songs' acoustic similarity.
  * **OpenVP** - Draws patterns to your music using the Open Visualization Platform.
  * **Radio Station Fetcher** - Fetch radio stations from shoutcast.com and xiph.org.
  * **Random By Lastfm** - Shuffle your library using information from the Last.fm online service.
  * **Stream Recorder** - Record internet-radio streams.
  * **Telepathy** - Browse your IM friends' music library, download or stream their tracks and share what you're listening to.
  * **Zeitgeist Dataprovider** - Publish your Banshee activities into Zeitgeist.

#### Getting Banshee Community Extensions

You can install the extensions listed above using one of the following methods.

  * Packages: its generally packaged in the same repository from which you get Banshee.  Look for the "banshee-community-extensions" package to install them all, or you can look for the individual banshee-extension-* packages if you only want a particular one.
  * [Source Tarballs](http://download.banshee-project.org/banshee-community-extensions/)
  * [Learn how to get and build it from git](http://banshee-project.org/contribute/write-extensions/)

### Third Party Extensions

The following extensions are developed by third-parties, and are not vetted or supported by the Banshee community.   In the future, Banshee will have a community repository that you'll be able to browse from within your Extension preferences.  But for now, you need to find and download them yourself, and install them in `~/.config/banshee-1/addins`.  Some of these extensions might also be available directly from certain Linux distributions.

#### Listening Post

Provides the basic functionality of sending e-mail messages to a preconfigured recipient when the track changes.  [More details](https://launchpad.net/banshee-listening-post)

#### Remote

Allows remote control of Banshee via the BansheeRemote application on Android phones.  [More details](https://launchpad.net/banshee-remote-plugin)
