---
layout: page
title: Audio CDs
show-sidebar: true
group: guide
order: 1
sidebar-group: guide
---

Banshee supports playing audio CDs and importing (ripping) them into your Music Library

### Playing Audio CDs

To play your CD, insert it into your drive.  It should automatically appear within Banshee in your sources list, beneath your Music Library and Video Library sources.  You can click the new source (named Audio CD, or the name of the album) and double click a track in it to begin playback.

### Importing/Ripping Audio CDs

  1. Insert a CD
  2. Banshee automatically detects it and adds it to the side menu; click it
  3. Uncheck any tracks you don't want imported
  4. Press the _Import CD_ button, located near the upper-right corner of Banshee
  5. Banshee will begin importing the CD.  As it finishes each track, it will appear in your _Music Library_

### Adjusting Your Preferences

You can change your CD importing preferences.  Go to the _Edit_ menu, and choose the _Preferences_ menu item.  Within the Preferences dialog, choose the _Source Specific_ tab and then select _Audio CDs_ in the list of sources.

 * ##### Import format
The defaults should be fine, but if you prefer to have your music imported as a certain file type (.mp3, .wma, or something else) or with certain quality settings (128kbps, 256kbps, etc) you can set that here.  If you don't see the file format you want, you need to ensure you have the appropriate GStreamer plugin/codec installed.

 * ##### Automatic import
With this item checked, Banshee will automatically begin importing as soon as you insert an audio CD - unless it can't find the track list (album name, track titles) for it, or it detects you already have at least part of the album imported.

 * ##### Eject when done importing
If you want Banshee to automatically eject your audio CDs after importing them, check this.
