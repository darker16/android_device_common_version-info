## Automatic TWRP versioning repo

# Features
* auto increment twrp patch number
* rename twrp recovery.img to twrp_A.B.C-d_$(CUSTOM_TWRP_VERSION_PREFIX)-YYYYMMDD-pp-$(TARGET_DEVICE).img

## How to use
Sync repo to device/common/version-info.

Add the following lines at the end of BoardConfig.mk in your device tree:

```
# Custom TWRP Versioning
# version prefix is optional - the default value is "LOCAL" if nothing is set in device tree
CUSTOM_TWRP_VERSION_PREFIX := CUSTOM

include device/common/version-info/custom_twrp_version.mk

ifeq ($(CUSTOM_TWRP_VERSION),)
CUSTOM_TWRP_VERSION := $(shell date -u +%Y%m%d)-01
endif
```
