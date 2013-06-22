---
layout: page
title: Write Extensions
show-sidebar: true
group: contribute
order: 5
sidebar-group: contribute
---

### Introduction

Banshee is very easy to extend.  Its object-oriented C# codebase is modular and organized, if large.

Some Banshee extensions are included in the Banshee codebase, either because they're relatively basic (eg Audio CD support, the Play Queue, Podcasts suport, etc), or because their authors did the magic dance (bug filing, patch submission, style matching, iterations, etc) required.  A simpler alternative is to create a new extension within Banshee Community Extensions (BCE), a looser, lower-barrier way of developing extensions.

BCE is hosted on Gitorious, a free git hosting provider.  Anybody can create an account there and clone the BCE repo and push their commits - right now, without asking anybody.

### Create a Working Extension - Right Now!

It's ludicrously easy to make a new extension.  Just follow these steps, and within a few minutes you'll be running your new, working extension.

  1. Install the latest version of Banshee, including any _devel_ packages; (the [latest git master](http://banshee-project.org/download/development/) should work great too!  Though you'll need to `make install` it.)
  2. Install a few extra build tools by running these [Build From Source commands](http://banshee-project.org/download/development/)
  3. Install [MonoDevelop 2.2.1](http://monodevelop.com/Download) or higher _(optional)_
  4. Open a Terminal application, and run these commands:

        git clone git://gitorious.org/banshee-community-extensions/banshee-community-extensions.git
        cd banshee-community-extensions
        ./create-extension Foo
        make run

This creates, builds, and runs Banshee with your extension.  Go to _Edit » Preferences » Extensions_ to enable it, and see it appear:

<center>
<img src="/images/banshee-community-extensions-foo.png" alt="Screenshot of Banshee showing the newly created Foo extension listed in Preferences > Extensions, and also in the source list">
</center>

You can now open, edit, and run your Extension in MonoDevelop: simply open the `Extensions.sln` file in the top directory of your BCE clone.

Resources:

  * [Writing code for Banshee (style guide, etc)](http://banshee-project.org/contribute/write-code/)
  * [GNOME's Git guide](http://live.gnome.org/Git)
  * [Get in touch with the Banshee community!](http://banshee-project.org/about/contact/)

### Getting Commit Access to BCE

Before we give you commit/push access to the BCE repo itself (and not just your clone), we'll want to see some of your work.  Send out a short e-mail/post to the mailing list/forum or join us on IRC asking for a review of your code, and that you'd like commit access - should be no problem!
