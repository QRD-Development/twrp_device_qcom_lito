# TWRP for Qualcomm Reference Design 750 / 765 (lito for arm64)

## Compile

Download the minimal-manifest-twrp/platform_manifest_twrp_aosp twrp-11 tree as described at https://github.com/minimal-manifest-twrp/platform_manifest_twrp_aosp#readme

Add this device repository to a new local manifest (`.repo/local_manifests/roomservice.xml`):

```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
  <project name="Edward-Recovery-Lab/android_device_qcom_lito" path="device/qcom/lito" remote="github" revision="twrp-11" />
</manifest>
```

Then sync the sources again:

```
repo sync
```

And finally compile it:

```
export ALLOW_MISSING_DEPENDENCIES=true
. build/envsetup.sh
lunch twrp_lito-eng
m recoveryimage
```

To test it:

```
fastboot boot out/target/product/lito/recovery.img
```

or

```
fastboot flash recovery out/target/product/lito/recovery.img
```
