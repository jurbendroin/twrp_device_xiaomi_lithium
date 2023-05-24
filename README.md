TWRP device configuration for Xiaomi Mi Mix
=========================================

The Xiaomi Mi Mix (codenamed _"Lithium"_) is a high-end smartphone from Xiaomi.

It was announced in October 2016. Release date was November 2016.

## Device specifications

Basic   | Spec Sheet
-------:|:-------------------------
CPU     | Quad-core (2x2.35 GHz Kryo & 2x2.19 GHz Kryo)
Chipset | Qualcomm MSM8996 Snapdragon 821
GPU     | Adreno 530
Memory  | 4/6 GB RAM
Shipped Android Version | 6.0.1
Storage | 128/256 GB
Battery | Li-Po 4400mAh battery
Display | 1080 x 2040 pixels, 6.4 inches (~362 ppi pixel density)
Camera  | 16 MP, f/2.0, EIS (gyro), phase detection autofocus, dual-LED (dual tone) flash

## Compile

First checkout minimal twrp with omnirom tree:

```
repo init -u git://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp.git -b twrp-12.1
repo sync
```

Then add these projects to .repo/manifest.xml:
```
<project path="device/xiaomi/lithium" name="jurbendroin/twrp_device_xiaomi_lithium" remote="github" revision="android-12.1" />
```
Finally execute these:
```
. build/envsetup.sh
lunch twrp_lithium-eng
export ALLOW_MISSING_DEPENDENCIES=true # Only if you use minimal twrp tree.
mka recoveryimage
```
To test it:
```
fastboot boot out/target/product/lithium/recovery.img
```

## Thanks

- Thanks to https://github.com/lithium-4-4-project/twrp_device_xiaomi_lithium
- Thanks to https://github.com/TeamWin/android_device_xiaomi_ginkgo
