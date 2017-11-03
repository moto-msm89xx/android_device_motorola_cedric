# Squid TWRP tree for Motorola MSM8937 Family

## Dependencies:
(you probably don't need most of these)
```
sudo apt-get install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop openjdk-6-jdk openjdk-6-jre pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev
sudo apt-get install g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev
```
You also need the repo tool for cloning Android source trees.

## Set up and get the repo:
```
mkdir ~/omni-twrp-tree
cd ~/omni-twrp-tree
repo init -u https://github.com/sultanqasim/twrp_recovery_manifest.git -b android-7.1
mkdir -p .repo/local_manifests
```
Create a file .repo/local\_manifests/motorola.xml and paste this in
```
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
    <project name="moto8937-twrp/android_device_motorola_msm8937-common" path="device/motorola/msm8937-common" remote="github" revision="twrp" />
    <project name="moto8937-twrp/android_device_motorola_addison" path="device/motorola/addison" remote="github" revision="twrp" />
    <project name="moto8937-twrp/android_device_motorola_albus" path="device/motorola/albus" remote="github" revision="twrp" />
    <project name="moto8937-twrp/android_device_motorola_cedric" path="device/motorola/cedric" remote="github" revision="twrp" />
    <project name="moto8937-twrp/android_device_motorola_montana" path="device/motorola/montana" remote="github" revision="twrp" />
    <project name="moto8937-twrp/android_device_motorola_owens" path="device/motorola/owens" remote="github" revision="twrp" />
    <project name="moto8937-twrp/android_device_motorola_perry" path="device/motorola/perry" remote="github" revision="twrp" />
    <project name="moto8937-twrp/android_device_motorola_potter" path="device/motorola/potter" remote="github" revision="twrp" />
    <project name="moto8937-twrp/android_device_motorola_sanders" path="device/motorola/sanders" remote="github" revision="twrp" />
    <project name="moto8937/android_kernel_motorola_msm8937" path="kernel/motorola/msm8937" remote="github" revision="cm-14.1" />
    <project name="LineageOS/android_device_qcom_common" path="device/qcom/common" remote="github" revision="cm-14.1" />
</manifest>
```

Now fetch the code
```
repo sync
```

## Building:
```
source build/envsetup.sh
breakfast perry # or your device
make clean
make -j30 recoveryimage
```
