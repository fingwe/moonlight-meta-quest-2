# Moonlight Android Fork
# Moonlight Meta Quest 2 ( Unofficial )

Notice, I don't plan on maintaining this branch,  i just forked it for my needs. So don't bother opening pull request and such.

I may , or may not pull again from the main moonlight repo. 

You are free to refork this and do what you want as long as it respect original repo terms and conditions.

[![AppVeyor Build Status](https://ci.appveyor.com/api/projects/status/232a8tadrrn8jv0k/branch/master?svg=true)](https://ci.appveyor.com/project/cgutman/moonlight-android/branch/master)
[![Translation Status](https://hosted.weblate.org/widgets/moonlight/-/moonlight-android/svg-badge.svg)](https://hosted.weblate.org/projects/moonlight/moonlight-android/)

[Moonlight for Android](https://moonlight-stream.org) is an open source client for NVIDIA GameStream and [Sunshine](https://github.com/LizardByte/Sunshine).

Moonlight for Android will allow you to stream your full collection of games from your Windows PC to your Android device,
whether in your own home or over the internet.

Moonlight also has a [PC client](https://github.com/moonlight-stream/moonlight-qt) and [iOS/tvOS client](https://github.com/moonlight-stream/moonlight-ios).

You can follow development on our [Discord server](https://moonlight-stream.org/discord) and help translate Moonlight into your language on [Weblate](https://hosted.weblate.org/projects/moonlight/moonlight-android/).

## Downloads
* [Google Play Store](https://play.google.com/store/apps/details?id=com.limelight)
* [Amazon App Store](https://www.amazon.com/gp/product/B00JK4MFN2)
* [F-Droid](https://f-droid.org/packages/com.limelight)
* [APK](https://github.com/moonlight-stream/moonlight-android/releases)

## Building
* Install Android Studio and the Android NDK
* Run ‘git submodule update --init --recursive’ from within moonlight-android/
* In moonlight-android/, create a file called ‘local.properties’. Add an ‘ndk.dir=’ property to the local.properties file and set it equal to your NDK directory.
* Build the APK using Android Studio or gradle

## Authors

* [Cameron Gutman](https://github.com/cgutman)  
* [Diego Waxemberg](https://github.com/dwaxemberg)  
* [Aaron Neyer](https://github.com/Aaronneyer)  
* [Andrew Hennessy](https://github.com/yetanothername)

Moonlight is the work of students at [Case Western](http://case.edu) and was
started as a project at [MHacks](http://mhacks.org).

## Changes in the fork

# app/src/main/AndroidManifest.xml

Fix to start the app in landscape mode

Changed for
- .PcView
- .ShortcutTrampoline
- .AppView
- .Game

<activity
    android:exported="true"
    android:resizeableActivity="true"
    android:screenOrientation="landscape" 
    ... />

# app/src/main/java/com/limelight/utils/UiHelper.java

Fix to prevent the app from crashing because Meta Quest 2 OS don't have the GameManager dependencies despite being an android version sufficient for having it.
Meta removed this from the Meta Quest OS.

private static void setGameModeStatus
...
if (gameManager == null) {
                return;
            }
...

So if gameManager variable is null, just return instead of crashing.
