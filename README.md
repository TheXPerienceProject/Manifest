![xperience](https://i.imgur.com/h4CgRmp.png)

Getting Started The XPerience Project
---------------
You must be running a 64-bit Linux distribution and must have installed some packages to build
The XPerience Project. Google recommends using [Ubuntu](http://www.ubuntu.com/download/desktop) for
this and provides instructions for setting up the system (with Ubuntu-specific commands) on
[the Android Open Source Project website](https://source.android.com/source/initializing.html#setting-up-a-linux-build-environment).

To initialize your local repository using the XPerience trees, use a command like this:

      $ mkdir xperience
      $ cd xperience
      $ repo init -u https://github.com/TheXPerienceProject/Manifest -b xpe-13.0
    
Then to sync up:

      repo sync -j<number_of_threads>
OR:
      repo sync --no-tags --no-clone-bundle --force-sync -c

--------

## Building The XPerience Project for your device

### Build Environment

- Tested and Working on any version of Ubuntu - 15.10 & 16.04 16.10 (64-bit)
- Any other distribution based of the Ubuntu Distro such as Lubuntu, Xubuntu and etc.
- A Terminal window
- A Good specs of hardware like 8 GB of RAM and an Intel I3 dual core (Minimum)
- A storage unit of any kind (minimum 200 GB). It would be better to use SSD because is more fast during the compliation process
- Some dependencies that should be installed

### [Dependencies for Linux](https://github.com/TheXPerienceProject/Manifest/wiki/Dependencies-for-Linux) or [Dependencies for Mac](https://github.com/TheXPerienceProject/Manifest/wiki/Dependencies-for-Mac)

### Building The XPerience Project ROM for your device
- Preparing Required Binaries and Device Drivers
- Set CCache for Faster Building (Optional)
- Build phase

### Set CCache

      $ export USE_CCACHE=1
      $ prebuilts/misc/linux-x86/ccache/ccache -M 50G

Congratulations,the sources are initialized! 
	  
#### To build The XPerience Project ROM

The bundled builder tool `./rom-build.sh` handles all the building steps for the specified device
automatically. As the device value, you just feed it with the device codename (for example,
'Addison' for the Moto Z Play).

      # Automatic script
      $ ./rom-build.sh codename
      # Example
      $ ./rom-build.sh addison

#### OR
      
      # Manually
      $ . build/envsetup.sh
      $ lunch codename-userdebug #only if we support your device if not clone manually and do
      $ lunch xpe_codename-userdebug or breakfast codename
      $ make bacon -j<number_of_threads>

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

## Copyright (C) 2018 The XPerience Project
