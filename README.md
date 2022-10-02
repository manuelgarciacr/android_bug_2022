Build: AI-213.7172.25.2113.9014738, 202208312042, 

AI-213.7172.25.2113.9014738, JRE 11.0.13+0-b1751.21-8125866x64 JetBrains s.r.o., OS Windows 10(amd64) v10.0 , screens 2880.0x1620.0

AS: Dolphin | 2021.3.1
Kotlin plugin: 213-1.7.10-release-for-android-studio-AS6777.52
Android Gradle Plugin: 7.3.0
Gradle: 7.4
Gradle JDK: version 11.0.13
NDK: from local.properties: (not specified), latest from SDK: 22.1.7171670
CMake: from local.properties: (not specified), latest from SDK: 3.6.0-rc2, from PATH: (not found)

### Steps to reproduce

Two launcher activities. The first one is not enabled with a boolean value:

```
// AndroidManifest.xml
android:enabled="@bool/enabled_false"

// bools.xml
<bool name="enabled_false">false</bool>
```
When I try to run the app, it gets installed, but fails to run (virtual and physical device):
```
Install successfully finished in 50 s 595 ms.
$ adb shell am start -n "eu.manuelgc.myapplication/eu.manuelgc.myapplication.MainActivity" -a android.intent.action.MAIN -c android.intent.category.LAUNCHER
Error while executing: am start -n "eu.manuelgc.myapplication/eu.manuelgc.myapplication.MainActivity" -a android.intent.action.MAIN -c android.intent.category.LAUNCHER
Starting: Intent { act=android.intent.action.MAIN cat=[android.intent.category.LAUNCHER] cmp=eu.manuelgc.myapplication/.MainActivity }
Error type 3
Error: Activity class {eu.manuelgc.myapplication/eu.manuelgc.myapplication.MainActivity} does not exist.

Error while Launching activity
Failed to launch an application on all devices
```
With a hardcoded boolean value, the execution succeeds:

```
// AndroidManifest.xml
android:enabled="false"
```
## Github example project

[Github project manuelgarciacr/android_bug_2022](https://github.com/manuelgarciacr/android_bug_2022.git)
