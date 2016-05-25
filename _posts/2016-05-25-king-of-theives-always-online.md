---
layout: post
title : Staying online 24x7 in King of Thieves - Android Auto Touch
categories : [Android, Hack]
---

This would be my first "own hack" for a game / app. I guess this is the kind of the things one would do when they are insomniac and hooked onto something.

The hack
-----------
This involves interacting with the game in an automated manner - basically touch something on the screen periodically. I wrote a simple script that does exactly this using [Android Debug Bridge][adb]. Yes, this is only for Android.

```bash
while true; do
adb shell input tap 139 1371
sleep 10
done
```

Requirements
-----------
1. Android device - duh!
2. PC - Linux / Mac. Windows works too, ask me how
3. ADB tools installed on the PC
4. USB debugging enabled on Phone


Find the touch point
-----------
1. Enable ```Developer options --> Show pointer location```
2. Launch King of Thieves app, select ```attack``` and then hold the ```castle icon``` at bottom left
3. Update ```x and y``` positions in the second line of the script above

How to use?
----------
1. Plugin the phone to PC
2. Run the script and goto sleep :)


[adb]: https://developer.android.com/studio/command-line/adb.html