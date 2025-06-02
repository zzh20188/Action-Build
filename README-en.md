**`Enlish`** | [简体中文](README.md)

[![Build](https://img.shields.io/badge/GitHub%20Actions-Build-181717?logo=github&logoColor=white&style=flat-square)](https://github.com/Numbersf/Action-Build/actions/workflows/Build%20SukiSU%20Ultra%20OnePlus.yml) [![Channel](https://img.shields.io/badge/Follow-Telegram-blue.svg?logo=telegram)](https://t.me/taichi91) [![OnePlus Kernel Manifest](https://img.shields.io/badge/OnePlus%20Kernel%20Manifest-EB0029?logo=oneplus&logoColor=white&style=flat-square)](https://github.com/OnePlusOSS/kernel_manifest)

# Action-Build
**```Build OnePlus SukiSU Ultra KPM Kernel```**
 
# Announcements
 
------
The ``_x`` suffix in the config file indicates the codename of the Android version you're using. For example, ``_w Android16, _v Android15, _u Android14, _t Android13, _s Android12``, and so on in reverse alphabetical **lowercase** order. A config **without a suffix** usually refers to the factory ``Android`` version of a model. Currently, only models with ``Android15`` (``_v``) are pre-listed. If you are using another version, please manually change ``_v`` to the corresponding code.
 
------
 
Regarding build time: generally, the older the model, the faster the build.
>***Using clang make (ultra-fast build)***
>>>-1.Known exceptions: some non-A15 models (e.g. OnePlus 11-A14)
 
>>`1h12min~1h14min,max:?`
>>>0.All
 
>>`22min~31min,max:35min`
 
>***Using official build.sh***
>>>-1.Known exceptions: some non-A15 models (e.g. OnePlus 11-A14)
 
>>`1h22min~1h28min,max:?`
>>>1.sm8450, sm8475, sm8550
 
>>`30~35min,max:45min`
>>>2.sm7675, sm7550, sm8650
 
>>`1h1min~1h12min,max:1h32min`
>>>3.sm8750
 
>>`2h1min~2h22min,max:2h45min`
> 

That is, if your build time exceeds the maximum listed above, please try rerunning the workflow and check the ``step`` to ensure it’s not an issue with the official process.
 
------
Some devices have issues with ``lz4kd``, currently under fix. **If the build fails, please don’t enable ``ZRAM algorithm`` yet.** Make sure to back up your ``boot.img`` in advance.
 
------
Remember to press **Volume Down** to install the module.
 
------
 
# Changelog
-- Support ultra-fast builds for some models `(currently supports 5.15, 6.1, 6.6)`  
-- Fixed OnePlus Ace5Pro and OnePlus 13 boot issues after build failure; using official dtbo now allows booting directly. [@reigadegr](https://github.com/reigadegr)  
-- Support displaying user-defined inputs during `Show selected inputs debug` step; workflow name will also reflect some values.  
-- Removed potential version codes from the suffix of `ak3.zip` config file, replaced with exact `Android` version numbers `XX.X.X`.
```
Examples:
AnyKernel3_SukiSUUltra_12896_oneplus_ace2pro_Android15.0.0_KPM_VFS.zip  
AnyKernel3_SukiSUUltra_12896_oneplus_13_Android15.0.2_KPM_VFS.zip  
AnyKernel3_SukiSUUltra_12896_oneplus_11_Android14.1.0_KPM_VFS.zip
```  
-- Allow custom kernel suffix.  <- **`beta`**
```
1. When the custom kernel suffix is empty, a random string is used instead of the default “x.xx.xxx-androidxx-8-o-g3b1e97b8b29f”
 
2. When custom suffix is enabled, the kernel version is modified to “x.xx.xxx-androidxx-[custom content]”, and the original “androidxx-8-o-g3b1e97b8b29f” is no longer retained.
```  
-- KPM is enabled by default and can no longer be disabled.  
-- New `dir4` and `dir5` paths added to support `sm8750` and some devices with new paths when ZRAM is enabled (such as `ace2p`, `13T`).   [@ShirkNeko](https://github.com/ShirkNeko)  
-- Added support for the `LZ4K` compression algorithm in the `zram` module.   [@ShirkNeko](https://github.com/ShirkNeko)  
-- Synchronized changes with the upstream download channel for the `susfs` module to fix download issues.  
-- Optimized the build scheme for `sm8750` and `sm7675`.  
-- New `dir3` path added to support `sm8475` (such as `ace2`).  
-- Support automatic download of latest `CI` version of `susfs` module and install via `ksud`; also automatically extracts manager `CI-APK` but does not install it.  
-- Supports `KPM` (copy without modifications) and `VFS HOOK` (optional).  