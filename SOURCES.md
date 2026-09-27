# Sources

## Stock firmware

Official Xiaomi Bigota:

https://bigota.miui.com/A15.0.16.0.VGWRUXM/serenity_ru_global-images-A15.0.16.0.VGWRUXM-user-20260817.0000.00-15.0-ru-a5218d4494.tgz

Build:

```text
A15.0.16.0.VGWRUXM
```

## Device tree / recovery

https://github.com/KSN2redawew/android_device_xiaomi_serenity-twrp

## LineageOS / Poco C71 community guide

https://github.com/barryC12/LineageOS-PocoC71

## Notes about this repository

The repository documents measurements and operations actually performed during the test session.

It intentionally does not claim that every community source is official, nor that an experimental patch is safe merely because it was built.

Large stock firmware archives are referenced by official URL and checksums instead of being copied into this repository.

## Reproducibility

When reproducing the work:

1. identify the exact model and codename;
2. verify the stock build;
3. download the stock ROM from the official source;
4. verify its MD5/SHA256;
5. make independent backups;
6. verify the device state before every destructive operation;
7. only then proceed with recovery/GSI/root experiments.
