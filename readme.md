Unoficial Mokee 44.2 for Sony Xperia U

Getting Started :

    curl http://commondatastorage.googleapis.com/git-repo-downloads/repo > /root/bin/repo
    chmod 755 /root/bin/repo
	mkdir mokee
    cd mokee
    repo init -u https://github.com/MoKee/android.git -b kk_mkt
    repo sync
    cd device
    mkdir sony
    cd sony
    git clone https://github.com/XperiaNovathor/android_device_sony_kumquat.git -b mokee-4.4 kumquat
    cd kumquat

Now connect your phone which have runing CM11 :

    ./extract-files.sh
    cd ../../..
    cd hardware
    git clone https://github.com/munjeni/android_hardware_semc.git -b master semc
    cd ..
    mkdir -p kernel/sony
    cd kernel/sony
    git clone https://github.com/munjeni/android_kernel_xperiago.git -b cm-11
    cd ../..

Patch android source code :

    patch -p1 < hardware/semc/patches/framework_av.patch
    patch -p1 < hardware/semc/patches/framework_native.patch
    patch -p1 < hardware/semc/patches/framework_base.patch
    patch -p1 < hardware/semc/patches/hardware_libhardware.patch
    patch -p1 < hardware/semc/patches/hardware_libhardware_legacy.patch
    patch -p1 < hardware/semc/patches/system_core.patch
    patch -p1 < hardware/semc/patches/bionic.patch
    patch -p1 < hardware/semc/patches/bootable_recovery.patch
    patch -p1 < hardware/semc/patches/external_bluetooth_bluedroid.patch
    patch -p1 < hardware/semc/patches/packages_apps_Bluetooth.patch


Our step is optional!!! Use only if you going to sync CM 11 source code daily, than simple revert each patch before you sync CM 11 source code :

    patch -p1 -R < hardware/semc/patches/framework_av.patch
    patch -p1 -R < hardware/semc/patches/framework_native.patch
    patch -p1 -R < hardware/semc/patches/framework_base.patch
    patch -p1 -R < hardware/semc/patches/hardware_libhardware.patch
    patch -p1 -R < hardware/semc/patches/hardware_libhardware_legacy.patch
    patch -p1 -R < hardware/semc/patches/system_core.patch
    patch -p1 -R < hardware/semc/patches/bionic.patch
    patch -p1 -R < hardware/semc/patches/bootable_recovery.patch
    patch -p1 -R < hardware/semc/patches/external_bluetooth_bluedroid.patch
    patch -p1 -R < hardware/semc/patches/packages_apps_Bluetooth.patch
    repo forall -p -c 'git checkout -f'
    repo sync
    Patch android source code :
    patch -p1 < hardware/semc/patches/framework_av.patch
    patch -p1 < hardware/semc/patches/framework_native.patch
    patch -p1 < hardware/semc/patches/framework_base.patch
    patch -p1 < hardware/semc/patches/hardware_libhardware.patch
    patch -p1 < hardware/semc/patches/hardware_libhardware_legacy.patch
    patch -p1 < hardware/semc/patches/system_core.patch
    patch -p1 < hardware/semc/patches/bionic.patch
    patch -p1 < hardware/semc/patches/bootable_recovery.patch
    patch -p1 < hardware/semc/patches/external_bluetooth_bluedroid.patch
    patch -p1 < hardware/semc/patches/packages_apps_Bluetooth.patch

You are ready to build :

    . build/envsetup.sh
    lunch mk_kumquat-userdebug
    make otapackage

ENJOY! 
