Before you start building OpenMW on Android you have to do few steps of preparation:
Download crystax ndk from https://www.crystax.net
Download and install [http://developer.android.com/sdk/index.html Google Android SDK]
Download [https://github.com/taka-no-me/android-cmake Cmake for Android] (it will be used for OpenMW and its dependencies compilation)
Java
http://www.oracle.com/technetwork/java/javase/downloads/index-jsp-138363.html

Download all OpenMW dependencies, ie:
OSG 
https://github.com/openscenegraph/osg
src/4578da5bf5b00fdf023b87e98099d647c5cb92ab?at=v1-9-0
Openal
http://repo.or.cz/w/openal-soft/android.git
boost
You can use boost 1.57 from crystax ndk
bullet
#https://github.com/bulletphysics/bullet3
Sdl2
https://www.libsdl.org/hg.php
ffmpeg
https://www.ffmpeg.org/download.html
mygui 3.2.1
https://github.com/MyGUI/mygui
zzip
zlib

Prebuilt openmw dependencies for armv7 arch
https://drive.google.com/file/d/0B5mOME9qjLFuWWl6YjF2TWc2bnc/view?usp=sharing

Compilation of OpenMW dependencies

Since my phone supports architecture armeabi-v7a I used this architecture for building. For example.
ndk-build APP_PLATFORM=android-14 APP_ABI=armeabi-v7a

Building OSG

http://www.openscenegraph.org/index.php/documentation/platform-specifics/android/43-building-openscenegraph-for-android-3-0-2

http://www.openscenegraph.org/index.php/documentation/platform-specifics/android/178-building-openscenegraph-for-android-3-4

Building MyGUI
Then you must build mygui with 1 render system

https://github.com/MyGUI/mygui

Building Bullet
Then you should build bullet. You can use cmake for it
https://github.com/bulletphysics/bullet3

Building OpenAL
Then you must build openal .
http://repo.or.cz/w/openal-soft/android.git

Building FFmpeg
Then you must build ffmpeg . Important! You must use ffmpeg 1.26: 
tutorial how to build ffmpeg for android
http://www.roman10.net/how-to-build-ffmpeg-with-ndk-r9/

Building SDL2
Then you must build SDL2: https://www.libsdl.org/hg.php
I used SDL2 mercurial latest source.

Building zzip
I used this library here
http://sourceforge.net/projects/ogre/files/ogre-dependencies-android/1.9/AndroidDependencies_27_08_2013.zip/download

Building zlip
I used this library from ndk  because this library is available in android

Building Openal
Then you must build openal .
http://repo.or.cz/w/openal-soft/android.git
Building OpenMW
Then I started to build OpenMW. 
I copied all  libraries  in one folder . For example AndroidDependencies
Also you must copy tis library to the same folder
and build openmw like this

cmake /home/sylar/openmw -DCMAKE_TOOLCHAIN_FILE=/home/sylar/android-cmake-master/android.toolchain.cmake 
-DOPENMW_DEPENDENCIES_DIR=/home/sylar/AndroidDependencies -DANDROID_NATIVE_API_LEVEL=14

After builing openmw library, you must copy all the libraries to libs folder in the  java project folder
for example :
 /eclipse-project/app/src/main/jniLibs/armeabi-v7a
Then you must import this java project in android-studio , which included with the android sdk.
Also you need to import the configuration files openmw.

