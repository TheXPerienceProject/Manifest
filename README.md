XPerience 9
============
This Rom Actually is based on AOSP , 
But contain alot of commits from CM and CAF , So I need say this roms is a hybrid rom

How to fetch and build
======================

 repo init -u https://github.com/XPerience-AOSP-Lollipop/Manifest -b xpe-9.1
 

<b>to build:</b>

. build/envsetup.sh

brunch devicename

example:

brunch falcon

Package final are on OUT folder


Special tutorial How to build on MAC OS (for example Mac OS yosemite 10.10.4)
=============================================================================

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
 
Setting a file descriptor limit
================================

On Mac OS, the default limit on the number of simultaneous file descriptors open is too low and a highly parallel build process may exceed this limit.
To increase the cap, add the following lines to your ~/.bash_profile:

# set the number of open files to be 1024
ulimit -S -n 1024

Downloading the source
======================
     cd /Volumes/android

     mkdir ~/bin
     PATH=~/bin:$PATH
     curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
     chmod a+x ~/bin/repo

     repo init -u https://github.com/XPerience-AOSP-Lollipop/Manifest -b xpe-9.1
     repo sync


NOTE:
=====
if you are old linux user and nano are familiar for you (like me xD) you need change this to

     git config --global core.editor nano
     
and you can use like linux commands :)


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
