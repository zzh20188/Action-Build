**Enlish** | [简体中文](README.md)

[![Build](https://img.shields.io/badge/GitHub%20Actions-Build-181717?logo=github&logoColor=white&style=flat-square)](https://github.com/Numbersf/Action-Build/actions/workflows/Build%20SukiSU%20Ultra%20OnePlus.yml) [![Channel](https://img.shields.io/badge/Follow-Telegram-blue.svg?logo=telegram)](https://t.me/taichi91) [![OnePlus Kernel Manifest](https://img.shields.io/badge/OnePlus%20Kernel%20Manifest-EB0029?logo=oneplus&logoColor=white&style=flat-square)](https://github.com/OnePlusOSS/kernel_manifest)

# Action-Build
**```Build OnePlus SukiSU Ultra KPM Kernel```**

# Announcement

The `_x` suffix in the config file indicates the Android version of your current system. `_v` means `Android15`, `_u` means `Android14`, `_t` means `Android13`, and no suffix usually refers to the device’s original `Android` version.
 
Some devices have issues with `lz4kd`, and a fix is in progress. **If the build fails, please do NOT enable the `ZRAM algorithm`**, and make sure to back up your `boot` partition in advance!
 
Special handling is required for `OnePlus Ace5Pro (ColorOS)` and `OnePlus 13 (ColorOS)`, and you must replace the `dtbo.img`.
 
Remember to install the module with **volume down**.
 
# Changelog
-- Temporarily fixed the build issue for `OnePlus Ace5Pro` and `OnePlus 13` [@reigadegr](https://github.com/reigadegr)   

-- Allow custom kernel suffix  <- **`beta`**
```
1. When the custom kernel suffix is empty, a random string is used instead of the default “x.xx.xxx-androidxx-8-o-g3b1e97b8b29f”
 
2. When custom suffix is enabled, the kernel version is modified to “x.xx.xxx-androidxx-[custom content]”, and the original “androidxx-8-o-g3b1e97b8b29f” is no longer retained.
```
-- KPM is enabled by default and can no longer be disabled.  
-- Supports indicating the corresponding `Android` version from the source code in the `ak3.zip`
```
AnyKernel3_SukiSUUltra_12866_oneplus_ace2pro_Android15_KPM_VFS.zip
```
-- New `dir4` and `dir5` paths added to support `sm8750` and some devices with new paths when ZRAM is enabled (such as `ace2p`, `13T`). [@ShirkNeko](https://github.com/ShirkNeko)   

-- Added support for the `LZ4K` compression algorithm in the `zram` module. [@ShirkNeko](https://github.com/ShirkNeko)   

-- Removed potential `_v` or `_u` suffixes in the configuration file.  
-- Synchronized changes with the upstream download channel for the `susfs` module to fix download issues.  
-- Optimized the build scheme for `sm8750` and `sm7675`.  
-- Fixed the version number error.  
-- New `dir3` path added to support `sm8475` (such as `ace2`).  
-- Supports automatic download of the latest `CI/Release` `susfs` module and uses `ksud` for installation.  
-- Supports `KPM` (copy without modifications) and `VFS HOOK` (optional).