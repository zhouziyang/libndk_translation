# `libndk_translation` prebuilts

Supports:
- Android 11 (`0.2.2`)
- Android 12 (`0.2.3`)

## Tips
```
# collect libndk_translation
{ find /system -name arm* -type d; find /system -name *ndk_translation*; find /system/etc -name *arm*; } \
    | tar -cf nb.tar -T -

# convert GNU to POSIX
bsdtar -cvf libndk_translation.tar --format=pax @nb.tar

# append libnb.so
find system -type l | tar -rf libndk_translation.tar -T -

# concatenate to existing tar
sudo tar -Af redroid-x86_64.tar libndk_translation.tar
```
