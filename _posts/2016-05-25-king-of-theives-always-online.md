---
layout: post
title : Staying online 24x7 in King of Thieves - Android Auto Touch
categories : [Tech]
---

This would be my first "own hack" for a game / app. I guess this is the kind of the things one would do when they are insomniac and hooked onto something.

The hack
-----------
This involves interacting with the game in an automated manner - basically touch something on the screen periodically. I wrote a simple script that does exactly this using [Android Debug Bridge][adb]. Yes, this is only for Android.

```bash
while true; do
adb shell input tap 1024 1076
sleep 3
adb shell input tap 945 812
sleep 3
done
```


How to use?
----------
1. Install [Android Debug Bridge][adb] on PC
2. Enable USB Debugging on phone and connect to PC
3. Run the script and goto sleep :)


Customization
---------
You can also choose your own touch points. Just enable ```Developer options --> pointer location" and launch King of Thieves to find the touch point co-ordinates for lines 2 and 4 in the script.

[adb]: https://developer.android.com/studio/command-line/adb.html