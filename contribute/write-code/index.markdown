---
layout: page
title: Write Code
show-sidebar: true
group: contribute
order: 4
sidebar-group: contribute
---

Banshee is written mostly in C# using Gtk#.  It is licensed under the [MIT/X11 free/open source software license](/about/license).  When you contribute to Banshee, you keep your copyright, but all contributions are licensed under the MIT/X11 license.

### Setting up Your Development Environment

To write code for Banshee, it's best if you have a copy of the [latest code](/download/development).

### Building Banshee

Building is straight forward and familiar if you've ever built software on Linux before. We use the standard autotools suite for our build environment. Once you have satisfied all the build dependencies, you're ready to build:
    
    $ cd banshee
    $ ./autogen.sh
    $ make
    $ make run

### Using MonoDevelop

After following the previous steps and getting Banshee to build from the command line, we recommend you use [MonoDevelop](http://monodevelop.org) to find your way around Banshee's source tree.  Even if you use another editor as your primary, having MonoDevelop open is very handy for finding where a class is declared and tracing a piece of code to its root.  Particularly useful are:

  * Search » Go to [type or file]
  * Right click on a variable or type and go to it's declaration, or find references
  * Autocomplete — Get the properties and methods for an object by typing "object_name." then ctrl-[space bar]

### New Features

Banshee is a large project, and to maintain its quality and usability, its maintainers have to make hard decisions about what to commit and maintain.  Havoc Pennington wrote a [great article](http://ometer.com/features.html) on the matter.

### Style Guidelines

Maintaining Banshee's code is easier when it all conforms to a single style guide.  Please follow [our guide](http://git.gnome.org/cgit/banshee/tree/HACKING) (see HACKING in our toplevel checkout directory) for all patches.

### Producing a Patch

Read about how to use git to [produce a patch](http://live.gnome.org/Git/Developers) on GNOME's git documentation.  Please commit to your local git branch, and then produce the patch using `git format-patch HEAD~1`, so that the patch includes your commit message and author information.

### Submitting Your Patch

If you have a patch that you would like committed to Banshee, the first step in the commit process is [opening a bug](http://bugzilla.gnome.org/enter_bug.cgi?product=banshee&version=git+master&bug_severity=enhancement) in Banshee's bugzilla. You must describe the patch, including any implications it has (good or bad).

Attach the patch to the bug report. Ensure you select the proper version (which in almost all cases should probably be git master) and the [severity](http://bugzilla.gnome.org/page.cgi?id=bug-status.html#bug_severity). If the patch adds a new feature, the severity is enhancement.

The Banshee developers get e-mailed as soon as you file a bug, so there is no need to e-mail the banshee-list about it.

Everyone is encouraged to test and review [others' patches](https://bugzilla.gnome.org/page.cgi?id=patchreport.html&product=banshee) and to give their feedback on the bug entry.  After being sufficiently reviewed (including by at least one maintainer), the maintainer will commit the patch or ask you to commit it yourself.

### Documentation

We generate API documentation for Hyena and Banshee at build time.  It is kept in XML files in the docs/ subdirectory, and is bundled and installed such that you can view it in the Monodoc tool.  You can help fill out the generated docs with a personal touch and more information by editing it within Monodoc.  When you're done editing, you can go back to your Banshee build directory and run `make merge-docs` and then submit the changes as a patch, attached to a bug report as per usual.

  * [DBus Interfaces](/contribute/write-code/dbus-interfaces)
