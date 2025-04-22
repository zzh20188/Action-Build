**Enlish** | [简体中文](README.md)
 
[![Build](https://img.shields.io/badge/GitHub%20Actions-Build-181717?logo=github&logoColor=white&style=flat-square)](https://github.com/Numbersf/Action-Build/actions/workflows/Build%20SukiSU%20Ultra%20OnePlus.yml) [![Channel](https://img.shields.io/badge/Follow-Telegram-blue.svg?logo=telegram)](https://t.me/taichi91) [![OnePlus Kernel Manifest](https://img.shields.io/badge/OnePlus%20Kernel%20Manifest-EB0029?logo=oneplus&logoColor=white&style=flat-square)](https://github.com/OnePlusOSS/kernel_manifest)
 
# Action-Build  
**```Build OnePlus SukiSU Ultra KPM Kernel```**
 
# Announcement  
Some devices have issues with ``lz4kd``, currently under investigation. **If it fails to boot, please do not enable ``lz4``**
 
Remember to install the module with **Volume Down**
 
# Changelog:  
- Remove any ```_v _u``` suffixes that may exist in the configuration file
- Synchronize the changes of the upstream download branch/tag of the ```susfs``` module to solve the problem of being unable to download
- Optimized ```build``` scheme for ```sm8750``` and ```sm7675```  
- Support for ```lz4kd``` (optional to enable)  
- Fixed version number error  
- Added ```dir3``` path to support ```sm8750``` (e.g., ```ace2```)  
- Supports automatic download and installation of the latest ```susfs``` module from ```CI/Release``` via ```ksud```  
- Supports ```KPM``` (no need for any modification or copying), and ```VFS HOOK``` (optional to enable)