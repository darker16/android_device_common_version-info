## Automatic TWRP versioning repo

# Features
* Auto increment twrp patch number
* Rename twrp boot/recovery.img to twrp_A.B.C_9-$(CUSTOM_TWRP_DEVICE_VERSION)_$(CUSTOM_TWRP_VERSION_PREFIX)-YYYYMMDD-pp-$(TARGET_DEVICE).img

## How to use
Sync repo to device/common/version-info.

Add the following lines at the end of BoardConfig.mk in your device tree:

```
# Custom TWRP Versioning
# device version is optional - the default value is "0" if nothing is set in device tree
CUSTOM_TWRP_DEVICE_VERSION := 0

# version prefix is optional - the default value is "LOCAL" if nothing is set in device tree
CUSTOM_TWRP_VERSION_PREFIX := CUSTOM

include device/common/version-info/custom_twrp_version.mk

ifeq ($(CUSTOM_TWRP_VERSION),)
CUSTOM_TWRP_VERSION := $(shell date +%Y%m%d)-01
endif
```

NOTE: The version number in TWRP will be the same as the renamed file.

