---
layout: page
title: Development
show-sidebar: true
group: download
sidebar-group: download
order: 2
---

Banshee's [git source code repository](http://git.gnome.org/cgit/banshee/) is generously hosted by the [GNOME](http://gnome.org/) project.

The most current version of the source is called `master`.  It can change minute by minute, and may not be stable at any given point.  In fact, it may cause data loss or other bad things.  You should only use it if you understand the risk.  Otherwise, you should stick with [official releases](/download).  Read more about [using git](http://live.gnome.org/Git/Developers).
	
  * Linux Instructions
  * Windows Instructions
  * OS X Instructions

### Building on Linux

You need to 1) install dependencies, 2) get the source, and then 3) build it.

#### 1. Install Dependencies

##### openSUSE 12.1 or higher

On openSUSE 12.1 you'll need to run the following commands to get all the build dependencies.

    sudo zypper in git autoconf automake libtool intltool gcc make
    sudo zypper si -d banshee

(Note: in older versions of openSUSE, like 11.0, the package name was "banshee-1", not "banshee".)

##### Ubuntu

On Ubuntu, you'll need to run the following commands to get all the build dependencies.

    sudo apt-get install git-core autoconf automake libtool intltool gcc make libgconf2.0-cil-dev libgconf2-dev
    sudo apt-get build-dep banshee
    sudo apt-get install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev

##### Fedora

On Fedora, you'll need to run the following commands to get all the build dependencies.

    sudo yum install git autoconf automake libtool intltool gcc make
    sudo yum-builddep banshee

#### 2. Get Source Code

Check out a copy of Banshee's git repository:
    
    git clone git://git.gnome.org/banshee

##### Other Libraries

You don't need to build and install these from source unless you want to hack on them, or if they are not provided by your distribution.

    git clone git://github.com/mono/taglib-sharp.git
    git clone git://github.com/mono/gio-sharp.git
    git clone git://github.com/mono/gtk-sharp-beans.git
    git clone git://github.com/mono/dbus-sharp.git
    git clone git://github.com/mono/dbus-sharp-glib.git

For the libgpod-based iPod support:

    git clone git://github.com/mono/gudev-sharp.git
    git clone git://github.com/mono/gkeyfile-sharp.git
    git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/libgpod

#### 3. Building, Running, and Installing

Then you should `cd banshee` (move to the folder where you checked it out from git) and run `./autogen.sh`.

If you want to use [MonoDevelop](http://monodevelop.com/), you can open `Banshee.sln` at this point

To build Banshee from the command line, run `make`.  You can run Banshee from git alongside Banshee from a package by not running `make install`.  Instead launch it with `make run`.

### Building on Windows

Banshee is easy to build on Windows.  We consider it to be in alpha, though -- it is not stable, well-tested, or polished, so use at your own risk and primarily if you're trying to help us improve it.  Follow these steps to get Banshee building:
	
  1. **Install Dependencies**
	
    * .NET 3.5 SP1 or higher
    * [msysgit](https://code.google.com/p/msysgit/downloads/detail?name=Git-1.7.4-preview20110204.exe) **with these options**:
      * _"Run Git from the Windows Command Prompt (only adds git to PATH)"_
      * _"Checkout Windows-style, commit Unix-style line endings"_
      * Optionally, install [TortoiseGit](http://code.google.com/p/tortoisegit/) for a GUI git environment
      * Github has a nice [guide for getting started with git](http://github.com/guides/using-git-and-github-for-the-windows-for-newbies) on Windows.

  2. **Download and run [checkout-banshee.bat](http://git.gnome.org/browse/banshee/plain/build/windows/checkout-banshee.bat)**
	
    * This script will clone Banshee from git (and a couple submodules).
    * You can double click it to run it.  It will check Banshee out into a `banshee` subfolder where the script is located.
	
  3. **Build Banshee**

    * With your favorite IDE ([MonoDevelop](http://monodevelop.com/) (FOSS, preferred), VisualStudio, SharpDevelop), **open `Banshee.sln`**. Make sure you select the "Windows" configuration.
    * Or run the `build\windows\build-banshee.bat` script, which calls `msbuild` directly

Report bugs and file patches according to the [normal process](/contribute).

### Building on OS X

It's quite easy to work on Banshee in Mac OS X. While resulting Banshee releases work on OS X 10.6 (Snow Leopard) and newer, Banshee must be built on OS X 10.7 or newer (Lion).

  1. **[Install XCode and the Developer Commandline Tools](http://developer.apple.com/devcenter/mac/)**

  2. **[Install Git](http://help.github.com/articles/set-up-git#platform-mac)**

  3. **Build Dependencies**

    * Takes hours, but only needs to be done infrequently  

          git clone git://github.com/Dynalon/bockbuild.git`  
          cd bockbuild/profiles/banshee`  
          ./darwin.py -bvd`

This process will likely take a few hours. Everything from GTK+, to GStreamer, to codecs, to Mono will be built in this process. When it's finished you'll be left with a full development environment for building and working on Banshee.

  4. **Build Banshee**

    * In the **same parent folder as bockbuild**, run  

          git clone git://git.gnome.org/banshee.git`  
          cd banshee`  
          ./bootstrap-bundle`  
          source darwin.env`  
          make`

You can also use MonoDevelop instead of using `make`. Open Banshee.sln **after** the `./bootstrap-bunde` step and build with MonoDevelop.
