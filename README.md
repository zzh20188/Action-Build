**简体中文** | [English](README-en.md)
 
# Action-Build
Build OnePlus SukiSU Ultra KPM Kernel
 
# 公告
部分设备的lz4存在问题,尝试修复中,**跑不出来请先不要使用lz4**
 
近期GitHub Action有问题,如果你在Initialize repo and sync这一步跑了超过5分钟,请果断**暂停**！
 
**Ace3V和Ace5有问题就多跑几次**
 
记得**音量下**安装模块,系统更新等无root状态使用**音量上**不安装模块
 
# 更新日志:
- 支持lz4kd（自选是否开启）
- 修复版本号错误
- 新增dir3用于支持sm8750(比如ace2)
- 支持自动下载最新CI/Release的susfs模块并调用ksud安装
- 支持KPM(无需任何修改复制什么的）
- 支持VFS HOOK（自选是否开启）
 
一加内核开源地址：[OnePlusOSS](https://github.com/OnePlusOSS/kernel_manifest)
