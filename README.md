# How-to-solve-gradle-task-assembledebug-failed-with-exit-code-1---fix-flutter-error

Flutter App stuck at “Running Gradle task 'assembleDebug'. SOLUTION
Running Gradle task 'assembleDebug'...(This is taking an unexpectedly long time.)
 
Open your flutter Project directory.
0:57​ Change directory to android directory in your flutter project directory cd android
01:05​ clean gradle    ./gradlew clean
01:10​ Build gradle     ./gradlew build or you can combine both commands with just ./gradlew clean build
01:46​ Now run your flutter project

OR

It usually happens with projects that were created in other machines.
To fix this on Android Studio on MAC, Follow these steps.

Open your Android Studio preferences(Command + ',') and go to Languages and Frameworks -> Dart
Check "Enable Dart support for the project your_project_name"
In "Dart SDK path" click in "…" and navigate to flutter SDK directory. Under that directory you'll find "bin/cache/dart-sdk". This is the dart sdk path you should use.
Click "Apply"
flutter packages get
flutter run



AND


If you still get error then here is what helped me:
delete .gradle and .m2 folders from $HOME directory, as well with in app folders: root/android/.gradle and root/build
flutter doctor
flutter clean
flutter packages pub cache clean
if you changed (as me) app icon then run:
flutter packages pub run flutter_launcher_icons:main
it will render icons for app - without it print same error with gradle..
Invalidate caches in Android Studio "File" > "Invalidate Caches / Restart..."


OR

Mac + Android Studio, in my case relatively special, following NOT work:
try flutter doctor -v but all environment is OK
set android.useAndroidX and android.enableJetifier to true
change android device: real phone xiaomi9 / emulator Nexus 5/ emulator Pixel 2
flutter clean
change minSdkVersion from 16 to 21
delete some (suspicious) dart code
and finally INDEED work by:
reboot my Mac
