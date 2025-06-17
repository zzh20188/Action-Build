**`简体中文`** | [English](README-en.md)
 
[![Build](https://img.shields.io/badge/GitHub%20Actions-Build-181717?logo=github&logoColor=white&style=flat-square)](https://github.com/Numbersf/Action-Build/actions/workflows/Build%20SukiSU%20Ultra%20OnePlus.yml) [![Channel](https://img.shields.io/badge/Follow-Telegram-blue.svg?logo=telegram)](https://t.me/taichi91) [![OnePlus Kernel Manifest](https://img.shields.io/badge/OnePlus%20Kernel%20Manifest-EB0029?logo=oneplus&logoColor=white&style=flat-square)](https://github.com/OnePlusOSS/kernel_manifest) [![Coolapk](https://img.shields.io/badge/Follow-Coolapk-3DDC84?style=flat-square&logo=android&logoColor=white)](http://www.coolapk.com/u/28259173)
 
# Action-Build
**```Build OnePlus SukiSU Ultra KPM Kernel```**
 
<details>
<summary><strong>点击查看如何fork项目</strong></summary>
<img src="https://github.com/Numbersf/Action-Build/blob/main/pic%2Fmake.gif" width="500"/>
</details>
 
<details>
<summary><strong>点击查看如何同步fork后的项目到最新</strong></summary>
<img src="https://github.com/Numbersf/Action-Build/blob/main/pic%2Fsyncfork.png" width="150"/>
<summary>请及时同步!某些更新可能会导致旧版本失效!</summary>
</details>
 
# 公告
 
------
> [!NOTE]
>配置文件中的``_x``后缀是你正在使用系统版本的代号。**倒序字母小写**。而无后缀的一般是一个机型的出厂``Android``版本。目前我只在预选中添加了``Android15``的机型也就是``_v``后缀,如果你在使用其他的安卓版本,请手动将``_v``改成其他代号
> <details>
> <summary><strong>点击查看详细的版本代号(部分未来可能会有改变)</strong></summary>
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
>关于要跑多久的问题 一般来说越往前的机型跑的速度越快
> <details>
> <summary><strong>点击查看使用极速编译clang make的用时</strong></summary>
>
>>>>0.已知的特殊机型:部分非A15机型(eg:一加11-A14;一加11-A13)
> 
>>>`1h8min~1h17min,max:1h17min`
>>>>0.其他所有机型
> 
>>>`22min~31min,max:35min`
> </details>
> 
> <details>
> <summary><strong>点击查看使用官方build.sh的用时</strong></summary>
>
>>>>0.已知的特殊机型:部分非A15机型(eg:一加11-A14;一加11-A13)
> 
>>>`1h14min~1h28min,max:1h28min`
>>>>1.sm8450、sm8475、sm8550
> 
>>>`30~35min,max:45min`
>>>>2.sm7675、sm7550、sm8650
> 
>>>`1h1min~1h12min,max:1h32min`
>>>>3.sm8750
> 
>>>`2h1min~2h22min,max:2h45min`
>> 
> </details>
>
>也就是说,如果你跑的时长超过了对应机型的最高时间,请尝试重新跑并查看``step``确保不是官方自己的问题
 
 
------
> [!CAUTION]
>请不要在**保``root``更新**时安装模块!  
>
>记得**音量下**安装模块!  
>
>如果你的机型是``sm8750``,并且曾经使用了官方脚本构建,而现在需要使用``Fast Build(极速构建)``,请先还原``dtbo.img、system_dlkm.erofs.img、vendor_dlkm.img、vendor_boot.img``**否则会无法开机!**  
>
>如果你开启了``ZRAM``算法,请在刷入``Anykernel3``重启**前**安装``ZRAM``模块,部分参数请自行调整。另外``5.10``内核暂不支持开启``ZRAM``算法,因为没有找到``zram.ko``路径  
>
>**我们注意到,``sm8650``的部分机型在更新``830/831``后内核小版本改变导致无法开机,请等待上游源码的更新**   

------
 
# 更新日志
--添加`TRUSTY_EXISTS`用于自动检测`6.6`内核是否内核源码存在缺陷,判断是否`sed`处理  
--支持**部分机型**开启风驰驱动(自选是否开启),驱动来自[@HanKuCha](https://github.com/HanKuCha)  
--删除`input`中除机型配置文件`FEIL`以外的所有其他机型参数并递推到`feil-map`以支持更多选择  
--当`ZRAM`开启时,自动下载并修改`ZRAM附加模块`,附加模块来自[@FURLC](https://github.com/FURLC)  
--修复`ZRAM`无法使用或者打不开非系统应用的问题  
--修复内核版本介于`5.15.0-5.15.123`之间官方脚本跑不出,极速编译结果有问题[@zzh20188](https://github.com/zzh20188)  
--支持`TCP拥塞控制算法(BBR)`  
--允许自定义内核后缀  <- **`beta`**  
```
1.当自定义内核后缀为空时,使用随机字符串,不再是默认的“x.xx.xxx-androidxx-8-o-g3b1e97b8b29f”
2.当自定义启用时,修改内核为“x.xx.xxx-androidxx-自定义内容”,同时也不再保留androidxx-8-o-g3b1e97b8b29f
3.当使用Fast Build(极速构建)时,为新的源内核信息x.xx.xxx-o-g3b1e97b8b29f添加缺失的内核android版本号,再进行1或2中的操作
```  
--支持部分机型极速编译`(目前支持5.10、5.15、6.1、6.6)`  
--修复`OnePlus Ace5Pro、OnePlus 13`跑不出来无法开机问题,直接使用官方dtbo就可以直接开机[@reigadegr](https://github.com/reigadegr)  
--支持显示自己填入的内容在`Show selected inputs debug`这一步,同时工作流名称也可以看到一些东西  
--从写入 `Anykernel3.zip` 的配置文件后缀中删除潜在的版本代码,替换成精确的 `Android` 版本号`XX.X.X`
```
AnyKernel3_SukiSUUltra_12896_oneplus_ace2pro_Android15.0.0_KPM_VFS.zip
AnyKernel3_SukiSUUltra_12896_oneplus_13_Android15.0.2_KPM_VFS.zip
AnyKernel3_SukiSUUltra_12896_oneplus_11_Android14.1.0_KPM_VFS.zip
``` 
--新增 `dir4`、`dir5` 路径用于支持 `sm8750` 和部分机型开启 `ZRAM` 后的新路径（比如 `ace2p`、`13T`）[@ShirkNeko](https://github.com/ShirkNeko)  
--添加 `zram` 模块的 `LZ4K` 压缩算法支持[@ShirkNeko](https://github.com/ShirkNeko)  
--同步 `susfs` 模块上游下载频道的变化，解决无法下载的问题  
--优化 `sm8750`、`sm7675` 的 `build` 方案  
--新增 `dir3` 路径用于支持 `sm8475`（比如 `ace2`）  
--支持自动下载最新 `CI/Release` 的 `susfs` 模块并调用 `ksud` 安装、自动获取管理器`CI-APK`解压到`Anykernel3`但不安装  
--支持 `KPM`（无需任何修改复制;自选是否开启）、`VFS HOOK`（自选是否开启）  
