**Enlish** | [简体中文](README.md)
 
# Action-Build  
**```Build OnePlus SukiSU Ultra KPM Kernel```**
 
OnePlus kernel open source address: [OnePlusOSS](https://github.com/OnePlusOSS/kernel_manifest)
 
# Announcement  
Some devices have issues with ``lz4kd``, currently under investigation. **If it fails to boot, please do not enable ``lz4``**
 
Remember to install the module with **Volume Down**
 
# Changelog:  
- Synchronize the changes of the upstream download branch/tag of the ```susfs``` module to solve the problem of being unable to download
- Optimized ```build``` scheme for ```sm8750``` and ```sm7675```  
- Support for ```lz4kd``` (optional to enable)  
- Fixed version number error  
- Added ```dir3``` path to support ```sm8750``` (e.g., ```ace2```)  
- Supports automatic download and installation of the latest ```susfs``` module from ```CI/Release``` via ```ksud```  
- Supports ```KPM``` (no need for any modification or copying), and ```VFS HOOK``` (optional to enable)