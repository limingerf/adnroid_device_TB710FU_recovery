# TWRP device tree for Lenovo Xiaoxin Pad Pro GT

TB710FU (codenamed _"topaz"_) is a smart tablet from Lenovo.

## Build it yourself?

```
mkdir twrp && cd twrp
repo init --depth=1 -u https://github.com/TWRP-Test/platform_manifest_twrp_aosp.git -b twrp-16.0
repo sync
git clone --depth=1 https://github.com/morannlx/adnroid_device_TB710FU_recovery.git device/lenovo/topaz
```

```
source build/envsetup.sh
lunch twrp_topaz
make recoveryimage
```

If there is no error, recovery.img will be found in `out/target/product/topaz/recovery.img `

The tree includes a pstore diagnostic helper and the production ramoops
settings observed on TB710FU (`0x9ffdff000`, 2 MiB).  `ramoops-overlay.dtbo`
is also produced by CI.  Apply that overlay to the production boot/vendor_boot
DTB before booting recovery; the recovery ramdisk is too late to change a
ramoops region after the kernel has probed it.  `pstore_diag` prints the
effective region and any files under `/sys/fs/pstore`.


## Features
Not works:
- Unknown

Works:
- [X] ADB
- [X] Display
- [X] OTA/Payload(full)
- [X] Decryption
- [X] Fasbootd
- [X] Flashing
- [X] MTP
- [X] Sideload
- [X] USB OTG

## To use it:

```
fastboot flash recovery recovery.img
or
fastboot flash recovery_a recovery.img
fastboot flash recovery_b recovery.img
```
