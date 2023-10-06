# `libndk_translation` prebuilts

Supports:
- Android 11 (`0.2.2`)
- Android 12 (`0.2.3`)
- Android 13 (`0.2.3`)
- Android 14 (`0.2.3`)

## How To Build
```
#####################################
### collect from Android Emulator ###
#####################################

# collect libndk_translation
{ find /system -name arm* -type d; find /system -name *ndk_translation*; find /system/etc -name *arm*; } \
    | tar -cf nb.tar -T -

# convert GNU to POSIX
bsdtar -cvf libndk_translation.tar --format=pax @nb.tar

# append libnb.so symlink
find system -type l | tar -rf libndk_translation.tar -T -


#####################################
####### collect from system.img #####
#####################################

# check system.img partition
fdisk system.img -l

# dump super.img
dd if system.img of super.img count=<END> skip=<START> bs=512

# unpack logic system partition
lpunpack -p system super.img super

# mount logic system partition
mount -o ro,loop system.img system

# collect libndk_translation
cd system
{ find system -name arm* -type d; find system -name *ndk_translation*; find system/etc -name *arm*; } \
    | tar -cf nb.tar -T -

# append libnb.so symlink
find system -type l | tar -rf libndk_translation.tar -T -
```
