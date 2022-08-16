![xperience](https://i.imgur.com/h4CgRmp.png)

[![Download XPerience](https://img.shields.io/sourceforge/dm/xperience-aosp?color=red&label=The%20XPerience%20Project%20Downloads&style=for-the-badge&labelColor=1B4F72&logo=sourceforge)](https://sourceforge.net/projects/xperience-aosp/files/)
[![Download XPerience](https://img.shields.io/sourceforge/dw/xperience-aosp?color=red&label=The%20XPerience%20Project%20Downloads&style=for-the-badge&labelColor=1B4F72&logo=sourceforge)](https://sourceforge.net/projects/xperience-aosp/files/)

Getting Started The XPerience Project
---------------
You must be running a 64-bit Linux distribution and must have installed some packages to build
The XPerience Project. Google recommends using [Ubuntu](http://www.ubuntu.com/download/desktop) for
this and provides instructions for setting up the system (with Ubuntu-specific commands) on
[the Android Open Source Project website](https://source.android.com/source/initializing.html#setting-up-a-linux-build-environment).

To initialize your local repository using the XPerience CAF trees, use a command like this:

      $ mkdir XPe
      $ cd XPe
      $ repo init -u https://github.com/TheXPerienceProject/Manifest -b xpe-17.0
      $ sudo install /usr/bin/repo .repo/repo/repo
    
Then to sync up:

      repo sync -c --force-sync --no-tags --no-clone-bundle -j$(nproc --all) --optimized-fetch --prune

--------

## Building The XPerience Project for your device

### Build Environment

- Tested and Working on any version of Ubuntu - 20.04 20.10 21.04 (64-bit)
- Tested and working on manjaro 
- Any other distribution based of the Ubuntu Distro such as Lubuntu, Xubuntu and etc.
- A Terminal window
- A Good specs of hardware like 16 GB of RAM (32GB recomended) and an Intel octacore or amd ryzen 12cores
- A storage unit of any kind (minimum 500 GB). It would be better to use SSD because is more fast during the compliation process
- Some dependencies that should be installed

### [Dependencies for Linux](https://github.com/TheXPerienceProject/Manifest/wiki/Dependencies-for-Linux) or [Dependencies for Mac](https://github.com/TheXPerienceProject/Manifest/wiki/Dependencies-for-Mac)

### Building The XPerience Project ROM for your device
- Preparing Required Binaries and Device Drivers
- Set CCache for Faster Building (Optional)
- Build phase

### Set CCache
 
      $ sudo apt-get install ccache
      $ export USE_CCACHE=1
      $ export CCACHE_DIR=~/.ccache
      $ ccache -M 50G

Congratulations,the sources are initialized! 
	  
#### To build The XPerience Project ROM
      
      $ . build/envsetup.sh
      $ lunch xperience_codename-userdebug
      $ make bacon -j$(nproc --all)

#### If you want build with GAPPS add this flag

      $ WITH_GMS := true

#### Credits to:

      * Android Open Source Project.
      * Cyanogenmod Team.
      * LineageOS
      * CodeAurora Forum
      * ParanoidAndroid (AOSPA)
      * And too much other's devs They do a lot for the community

      # bibliography:
      * http://tryge.com/2013/06/15/build-android-from-source-macosx/
      * https://source.android.com/source/initializing.html

## Copyright (C) 2011-2022 The XPerience Project
