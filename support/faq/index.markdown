---
layout: page
title: FAQ
long-title: Frequently Asked Questions
show-sidebar: true
group: support
order: 1
sidebar-group: support
---

### Features

**Where does Banshee get its cover art?**  
Banshee looks first in the audio file itself for embedded artwork, then in the folder the file is in, then from Rhapsody, then MusicBrainz, which may link to Amazon or other sites, then finally Last.fm.

**How do I get my compilation albums to group/sort nicely?**  
See the [user guide](/support/guide/track-list).

**Where can I find (and how do I install) third-party extensions?**  
See the [Extensions](/download/extensions) section.

**Does Banshee support audio/video format _X_ (mp3, aac, mpeg, etc)?**  
Banshee uses [GStreamer](http://www.gstreamer.net/) for audio and video decoding (playing) and encoding (ripping, format conversions).  Whatever codecs you have installed for GStreamer, Banshee will be able to use (with a small number of [exceptions](http://bugzilla.gnome.org/show_bug.cgi?id=524595)).

**Does Banshee run on Windows or OS X?**  
Yes.  See the [download](/download) page.

**What happened to my Last.fm streaming?**  
Last.fm put out a new API for programs to use, which we dutifully upgraded to.   Unfortunately, that API only lets paid subscribers stream.  The old API was supposed to be shut off long ago, but hasn't been, so apps still using it may still be able to stream for free.  We don't plan to revert to the old API.

### Hardware

**Does Banshee support iPhones or iPod Touch devices?**  
Yes, since the 1.7.5 release.

**What devices does Banshee support?**  
This answer is a work in progress - there are probably quite a few devices not mentioned here that may work with Banshee.  Try yours, and [let us know](/about/contact)!

MTP Devices

  * Many Creative brand devices (Zen V Plus)
  * Many Sansa brand devices
  * Probably others - list incomplete

Mass Storage Devices

  * Android phones (Nexus One, G1, Galaxy, Droid, Pulse)
  * Nokia N900
  * Palm Pre
  * Probably others - list incomplete

iPods - most iPods and iOS devices should work with Banshee.  Apple frequently updates the database format the devices use by upgrading iTunes, so it's recommended to use Banshee exclusively to manage your iPod, or not at all.  Importing music from an iPod managed with iTunes should be fine, though.

### Technical / Infrastructure

**Where does Banshee store configuration files/the library database?**  
It is stored under `~/.config/banshee-1/`.  The library database itself is called `banshee.db` and is a [SQLite](http://www.sqlite.org/) 3 database.

**I'm seeing errors saying that my database disk image is malformed. What should I do?**  
You have two options: try to recover your database or start anew.

To recover, quit Banshee and run these commands:

    $ cd ~/.config/banshee-1
    $ sqlite3 banshee.db ".dump" > dump
    $ mv banshee.db banshee.db.backup
    $ cat dump | sqlite3 banshee.db

Then start Banshee. If recovering didn't work, you can delete (or better backup) the database file and re-import your media. You might lose your ratings and playcounts.
