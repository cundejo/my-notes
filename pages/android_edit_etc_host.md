---
title: Android edit etc host
---

##
```shell
adb devices -l                 # make sure your gadget is listed
adb shell                      # run a shell there
su                             # become the root (don't miss confirmation request!)
mount -o remount,rw /system    # allow to write
vi /system/etc/hosts           #i to enter edit mode, ESC to out edit mode, :wx
mount -o remount,ro /system    # get things back to normal
exit                           # unroot
nslookup domain.com            # check if it works
exit                           # good bye
```
