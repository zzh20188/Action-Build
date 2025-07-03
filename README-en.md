**`Enlish`** | [简体中文](README.md)

[![Build](https://img.shields.io/badge/GitHub%20Actions-Build-181717?logo=github&logoColor=white&style=flat-square)](https://github.com/Numbersf/Action-Build/actions/workflows/Build%20SukiSU%20Ultra%20OnePlus.yml) [![Channel](https://img.shields.io/badge/Follow-Telegram-blue.svg?logo=telegram)](https://t.me/taichi91) [![OnePlus Kernel Manifest](https://img.shields.io/badge/OnePlus%20Kernel%20Manifest-EB0029?logo=oneplus&logoColor=white&style=flat-square)](https://github.com/OnePlusOSS/kernel_manifest) [![Coolapk](https://img.shields.io/badge/Follow-Coolapk-3DDC84?style=flat-square&logo=android&logoColor=white)](http://www.coolapk.com/u/28259173)

# Action-Build
**```Build OnePlus SukiSU Ultra KPM Kernel```**
<details>
<summary><strong>Click to view how to fork</strong></summary>
<img src="https://github.com/Numbersf/Action-Build/blob/SukiSU-Ultra/pic/make.gif" width="500"/>
</details>
<details>
<summary><strong>Click to view how to synchronize the forked project to the latest</strong></summary>
<p>
  <img src="https://github.com/Numbersf/Action-Build/blob/SukiSU-Ultra/pic/syncfork.png" width="150"/>
  <img src="https://github.com/Numbersf/Action-Build/blob/SukiSU-Ultra/pic/syncfork(2).png" width="150"/>
</p>
<summary>Please synchronize in time! Some updates may cause the old version to become invalid! If it still does not work after synchronization, please delete and re-fork! If there are still problems, please submit issues.</summary>
</details>

# Announcements

------
> [!NOTE]  
> The `_x` suffix in the config file corresponds to the code name of your current Android system version. The codes are in reverse alphabetical order and lowercase. A config without any suffix usually refers to the device’s stock Android version. Currently, only Android 15 (`_v`) variants are preset. If you are using a different version, please manually replace `_v` with the appropriate code.
> <details>
> <summary><strong>Click to view the Android version codes (subject to future updates)</strong></summary>
>
>>`_z Android19 (Zebra Cake)`
>
>>`_y Android18 (Yogurt Parfait)`
>
>>`_x Android17 (Xmas Pudding)`
>
>>`_w Android16 (Wedding Cake)`<strong>
>
>>`_v Android15 (Vanilla Ice Cream)`
>
>>`_u Android14 (Upside Down Cake)`
>
>>`_t Android13 (Tiramisu)`
>
>>`_s Android12 (Snow Cone)`</strong>
>
>>`_r Android11 (Red Velvet Cake)`
>
>>`_q Android10 (Quince Tart)`
>
>>`_p Android9 (Pie)`
>
>>`_o Android8 (Oreo)`
>
>>`_n Android7 (Nougat)`
>
>>`_m Android6 (Marshmallow)`
>
>>`_l Android5 (Lollipop)`
>
>>`_k Android4.4 (KitKat)`
>
>>`_j Android4.3–4.1 (Jelly Bean)`
>
>>`_i Android4.0 (Ice Cream Sandwich)`
>
>>`_h Android3.x (Honeycomb)`
>
>>`_g Android2.3 (Gingerbread)`
>
>>`_f Android2.2 (FroYo)`
>
>>`_e Android2.1 (Eclair)`
>
>>`_d Android1.6 (Donut)`
>
>>`_c Android1.5 (Cupcake)`
>
> </details>

------
> [!IMPORTANT]
>Regarding build duration: in general, the older the device model, the faster the compilation.
> <details>
> <summary><strong>Click to view build time using ultra-fast clang + make</strong></summary>
>
>|Device Type| Average Duration Range               | Maximum Duration|
>|--------------------------|-----------------------------|------------------|
>| `All` | `1st:19min ~ 35min 2nd:9min ~ 19min`| `42min` |
>|`OnePlus 11-A13、A14`|`1st:1h8min ~ 1h17min 2nd:50min ~ 1h10min`| `1h23min` |
>
>Using ccache may slow down the first build.
> </details>
>
> <details>
> <summary><strong>Click to view build time using official build.sh</strong></summary>
>
>|Device Type| Average Duration Range               | Maximum Duration|
>|--------------------------|-----------------------------|------------------|
>| `sm8450, sm8475, sm8550` | `29min ~ 35min`             | `45min`
>| `sm7675, sm7550, sm8650` |`59min ~ 1h12min`| `1h28min`        |
>| `sm8750`|`1h1min ~ 1h8min`| `1h24min`       |
>|`OnePlus 11-A13、A14`| `1h1min ~ 1h28min`  |`1h32min`|
>
></details>
>
>In other words, if your runtime exceeds the maximum expected duration for the target device, please pause and rerun the workflow while checking each step. Pay special attention to the “Initialize repo and sync” step — for all non-A15 devices (except for certain special cases), this step should complete within 10 minutes. If it takes longer, it may indicate an issue on GitHub's end. In that case, try rerunning the job. If the issue persists, please wait and try again later.

------
> [!CAUTION]
> Do **NOT** install modules during **root-preserving updates**!
>
> Remember to press **Volume Down** when installing the module!
>
> If your device is `sm8750`, and you previously used the official script to build,
> but now want to use `Fast Build`, please **restore** the following images first:
> `dtbo.img`, `system_dlkm(.erofs).img`, `vendor_dlkm.img`, and `vendor_boot.img`,
> **otherwise the device may fail to boot!**
>
> If you have enabled the `ZRAM` algorithm, make sure to install the `ZRAM` module
> **before rebooting** after flashing with `Anykernel3`. You may need to adjust some parameters manually.The 5.10 kernel is not supported `ZRAM` , as the `zram.ko` module path could not be found.
>
 
------
 
# Features in Development
- [ ] `ccache` supports AB update mode  
- [ ] Switching between different branches  
- Toothpaste should be squeezed bit by bit, GPUs should be cut slice by slice, PPTs should be shown slide by slide, and code should be written line by line — more features and optimizations... stay tuned!
 
# Changelog
-- First to support custom kernel build time `UTS_VERSION` for all device models and all build methods.  
-- Use `ccache` to speed up the workflow. It is only effective when `fast build` is enabled. The cache will need to be regenerated on first use, major updates, or when the key is changed, which may reduce the speed.  
-- Initial support for the sm8750's new setlocalversion format using echo, fixing the issue where custom and randomly-generated pseudo-official suffixes were not applied. Now, this feature is fully supported across all device models and build methods.  
-- Add `TRUSTY_EXISTS` to automatically detect whether the `6.6` kernel has defects in the kernel source code and determine whether `sed` is needed.  
-- Support enabling fongchi driver for selected devices (optional), driver from [@HanKuCha](https://github.com/HanKuCha).  
-- Remove all device-related parameters from `input` except the device config file `FEIL`, and propagate to `feil-map` to support more options.  
-- When `ZRAM` is enabled, automatically download and modify the ZRAM additional module, module from [@FURLC](https://github.com/FURLC).  
-- Fix issues where `ZRAM` is unusable or unable to launch non-system apps.  
-- Fix the problem that the official script cannot run when the kernel version is between `5.15.0-5.15.123`, and the result of the quick compilation has problems. [@zzh20188](https://github.com/zzh20188)  
-- Support for `TCP congestion control algorithm (BBR)`.  
-- Allow custom kernel suffix.  <- **`beta`**
```
1. When the custom kernel suffix is empty, a random string is used instead of the default “x.xx.xxx-androidxx-8-o-g3b1e97b8b29f”
2. When custom suffix is enabled, the kernel version is modified to “x.xx.xxx-androidxx-[custom content]”, and the original “androidxx-8-o-g3b1e97b8b29f” is no longer retained.
3. When using clang make (Fast Build), add the missing kernel android version number to the new source kernel information x.xx.xxx-o-g3b1e97b8b29f, and then perform operations in 1 or 2.
```  
-- Support fast-build `(5.10[Debut], 5.15[Debut], 6.1, 6.6)`  
-- Fixed OnePlus Ace5Pro and OnePlus 13 boot issues after build failure; using official dtbo now allows booting directly. [@reigadegr](https://github.com/reigadegr)  
-- Support displaying user-defined inputs during `Show selected inputs debug` step; workflow name will also reflect some values.  
-- Removed potential version codes from the suffix of `Anykernel3.zip` config file, replaced with exact `Android` version numbers `XX.X.X`.
```
Examples:
AnyKernel3_SukiSUUltra_12896_oneplus_ace2pro_Android15.0.0_KPM_VFS.zip  
AnyKernel3_SukiSUUltra_12896_oneplus_13_Android15.0.2_KPM_VFS.zip  
AnyKernel3_SukiSUUltra_12896_oneplus_11_Android14.1.0_KPM_VFS.zip
```   
-- Added support for the `LZ4K` compression algorithm in the `zram` module.   [@ShirkNeko](https://github.com/ShirkNeko)  
-- Synchronized changes with the upstream download channel for the `susfs` module to fix download issues.  
-- Optimized the build scheme for `sm8750` and `sm7675`.  
-- Support automatic download of latest `CI` version of `susfs` module and install via `ksud`; also automatically extracts manager `CI-APK` but does not install it.  
-- Supports `KPM` (copy without modifications;optional) and `VFS HOOK` (optional).  