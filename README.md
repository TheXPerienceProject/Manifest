# The XPerience Project #

## Setting up your machine ##

You must be running a 64-bit Linux distribution and must have installed some packages to build
The XPerience Project. Google recommends using [Ubuntu](http://www.ubuntu.com/download/desktop) for
this and provides instructions for setting up the system (with Ubuntu-specific commands) on
[the Android Open Source Project website](https://source.android.com/source/initializing.html#setting-up-a-linux-build-environment).

Once you have set up your machine according to the instructions by Google, return here and carry
on with the rest of the instructions.

## Grabbing the source ##

[Repo](http://source.android.com/source/developing.html) is a tool provided by Google that
simplifies using [Git](http://git-scm.com/book) in the context of the Android source.

### Installing Repo ###

```bash
# Make a directory where Repo will be stored and add it to the path
$ mkdir ~/.bin
$ PATH=~/.bin:$PATH

# Download Repo itself
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo

# Make Repo executable
$ chmod a+x ~/.bin/repo
```

### Initializing Repo ###

```bash
# Create a directory for the source files
# You can name this directory however you want, just remember to replace
# WORKSPACE with your directory for the rest of this guide.
# This can be located anywhere (as long as the fs is case-sensitive)
$ mkdir WORKSPACE
$ cd WORKSPACE

# Install Repo in the created directory
# Use a real name/email combination, if you intend to submit patches
$ repo init -u https://github.com/XPerience-AOSP-Lollipop/manifest -b xpe-11.1
```

### LINUX ###
### Downloading the source tree ###

This is what you will run each time you want to pull in upstream changes. Keep in mind that on your
first run, it is expected to take a while as it will download all the required Android source files
and their change histories.

```bash
# Let Repo take care of all the hard work
#
# The -j# option specifies the number of concurrent download threads to run.
# 4 threads is a good number for most internet connections.
# You may need to adjust this value if you have a particularly slow connection.
$ repo sync -j4
```

#### Syncing specific projects ####

In case you are not interested in syncing all the projects, you can specify what projects you do
want to sync. This can help if, for example, you want to make a quick change and quickly push it
back for review. You should note that this can sometimes cause issues when building if there is
a large change that spans across multiple projects.

```bash
# Specify one or more projects by either name or path

# For example, enter XPerience-AOSP-Lollipop/android_frameworks_base or
# frameworks/base to sync the frameworks/base repository

$ repo sync PROJECT
```

## Building ##

The bundled builder tool `./rom-build.sh` handles all the building steps for the specified device
automatically. As the device value, you just feed it with the device codename (for example,
'hammerhead' for the Nexus 5).

```bash
# Go to the root of the source tree...
$ cd WORKSPACE
# ...and run the builder tool.
$ ./rom-build.sh DEVICE
```

### Mac OS X ###
# Special tutorial How to build on MAC OS (for example Mac OS yosemite 10.10.4) #

<b>Creating a case-sensitive disk image</b>

You can also create it from a shell with the following command:

     hdiutil create -type SPARSE -fs 'Case-sensitive Journaled HFS+' -size 60g ~/android.dmg

This will create a .dmg (or possibly a .dmg.sparsefile) file which, once mounted, acts as a drive with the required formatting for Android development.

If you need a larger volume later, you can also resize the sparse image with the following command:

     hdiutil resize -size <new-size-you-want>g ~/android.dmg.sparseimage

For a disk image named android.dmg stored in your home directory, you can add helper functions to your ~/.bash_profile:
To mount the image when you execute mountAndroid:

 *mount the android file image
       function mountAndroid { hdiutil attach ~/android.dmg -mountpoint /Volumes/android; }

Note: If your system created a .dmg.sparsefile file, replace ~/android.dmg with ~/android.dmg.sparsefile.
To unmount it when you execute umountAndroid:

# unmount the android file image
     function umountAndroid() { hdiutil detach /Volumes/android; }

Once you've mounted the android volume, you'll do all your work there. You can eject it (unmount it) just like you would with an external drive.

Install MacPorts from [macports.org] (http://www.macports.org/install.php.)
 in terminal write:
 
    export PATH=/opt/local/bin:$PATH

    POSIXLY_CORRECT=1 sudo port install gmake libsdl git gnupg

if you use mac os 10.4 also install this

    POSIXLY_CORRECT=1 sudo port install bison
 
# Setting a file descriptor limit #

On Mac OS, the default limit on the number of simultaneous file descriptors open is too low and a highly parallel build process may exceed this limit.
To increase the cap, add the following lines to your ~/.bash_profile:

# set the number of open files to be 1024
ulimit -S -n 1024

## Downloading the source ##

     cd /Volumes/android

     mkdir ~/bin
     PATH=~/bin:$PATH
     curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
     chmod a+x ~/bin/repo

     repo init -u https://github.com/XPerience-AOSP-Lollipop/Manifest -b xpe-11.0
     repo sync


# NOTE: #

if you are old linux user and nano are familiar for you (like me xD) you need change this to

     git config --global core.editor nano
     
and you can use like linux commands :)

#NOTE 2 #


if you have problems related to gnu-sed ("GNU sed is required for Darwin builds, please install and add 'gsed' to the path")


install brew and follow this
tap in terminal:

    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

ow, we need to run a few commands through Brew, just to make sure everything is installed correctly. Enter the following into the Terminal:
Code:
     brew outdated && brew update && brew upgrade && brew doctor

now you can use brew

     brew install gnu-sed gnupg pngcrush

Now for build you need MAVEN is easy install on linux but on mac YOU need homebrew installed then

     brew install maven

Needed to execute some GNU binary

     brew install coreutils

## Using our assets ##

### Code ###

Our codebase is licensed under Apache License, Version 2.0 unless otherwise specified. Apache
License 2.0 allows a variety of actions on the content as long as licensing and copyright
notices are retained and included with the code and your changes to the codebase are stated.

You can read the full license text at http://www.apache.org/licenses/LICENSE-2.0

### Images & other assets ###

Unless otherwise specified, all our assets, including but not limited to images, are licensed
under Creative Commons Attribution-NonCommercial 4.0 International, or CC BY-NC 4.0 for short.
This means that you are allowed to modify the aforementioned assets in any way you want and
you are free to share the originals and/or the modified work. However, you are not allowed
to use the assets for commercial purposes and you must provide attribution at all times which
means you have to include a short note about the license used (CC BY-NC 4.0), the original
author/authors (The XPerience Project Project or XPe) and inform about any changes that have been
made. A link to the [website](http://klozz.github.io/git.klozz.personal/) should usually be included as well.

You can reach the full legal text at http://creativecommons.org/licenses/by-nc/4.0/

Credits to:
=============

Android Open Source Project.

Cyanogenmod Team.

CodeAurora Forum

And too much other's devs 
They do a lot for the community

Developers:
TeamMEX

bibliography:
http://tryge.com/2013/06/15/build-android-from-source-macosx/
https://source.android.com/source/initializing.html