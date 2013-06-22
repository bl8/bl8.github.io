---
layout: page
title: File Bugs
show-sidebar: true
group: contribute
order: 1
sidebar-group: contribute
---

Banshee uses an issue tracker called Bugzilla for bug reports.

Before filing a bug, please try to check if it's already been filed.  Here is a [list of recent bugs with duplicates](https://bugzilla.gnome.org/buglist.cgi?chfieldfrom=2011-01-01&chfieldto=Now&longdesc=has%20been%20marked%20as%20a%20duplicate%20of%20this%20bug&longdesc_type=substring&product=banshee&query_format=advanced&order=bug_id%20DESC).

The GNOME project has a page describing [how to write good bug reports](http://bugzilla.gnome.org/page.cgi?id=bug-writing.html).

When you're ready, [file your bug report](http://bugzilla.gnome.org/enter_bug.cgi?product=banshee).

If your bug involves unexpected behavior, a crash, or an error of any kind, it's a good idea to attach the Banshee log to the bug you file.  To get this log file, please follow the instructions for your operating system.

**On Linux and Mac OS X**, open a terminal and run this command:

    kill -s QUIT $(pidof banshee); cp ~/.config/banshee-1/log ~/Desktop/banshee.log

and attach the banshee.log file that is now on your Desktop.  The `kill -s QUIT` part of that command doesn't actually close Banshee; it tells Banshee to output more information useful for debugging.

**On Windows**, open a command prompt and run this command:

    copy "%APPDATA%\banshee-1\banshee.log" "%USERPROFILE%\Desktop\banshee_log.txt"

and attach the banshee_log.txt file that is now on your Desktop.

If you enjoy helping make Banshee better by submitting bugs, you can get more involved by [helping others with their bug reports](/contribute/help-with-bug-reports/).
