# Lenovo-M900-Tiny-Hackintosh-Sequoia
## 联想 ThinkCentre M900 macOS15 Sequoia 完美黑苹果



#### 这份EFI文件基于[Lenovo-ThinkCentre-M900-Tiny-Hackintosh-Sequoia](https://github.com/tyl3rsleeps/Lenovo-ThinkCentre-M900-Tiny-Hackintosh-Sequoia)。
原作者的配置文件的问题在于无法驱动Intel网卡，也没有解锁CFG Lock。

<br />

### 适用机型：联想M900。M700、NEC6也可以用（未经过测试）。

<br />

### 完成度：

#### 基本完美。Intel网卡成功驱动，Wi-Fi蓝牙正常使用，Airdrop可以单向投送到其他设备。     

#### 睡眠唤醒没有问题。核显加速没有问题。HDMI输出没有问题。M900可以使用NVME SSD。
<br />

### 我的联想M900配置：

- ##### 主板型号：Lenovo 30B0（Intel Q170芯片组）
- ##### CPU: Intel i5-6500T @ 2.5GHz
- ##### GPU: Intel HD Graphics 530 （核显）
- ##### 内存：8GB DDR4 @ 2133MHz
- ##### BIOS版本：官方2022年7月，[FWKTBFA](https://pcsupport.lenovo.com/us/en/products/desktops-and-all-in-ones/thinkcentre-m-series-desktops/thinkcentre-m900/downloads/ds105487-flash-bios-update-intel-b150-for-thinkcentre-m700-tiny-thinkcentre-m800-m900-m900x-tiny)
- ##### 网卡：Intel Dual Band Wireless-AC 8260
- ##### 其他：HDMI拓展模块 (实际也是从DP信号转到HDMI信号)
- ##### M.2 NVME SSD 京造麒麟512GB

<br />

## 使用方法：

###### （建议在安装macOS前先安装Windows）
### 一、安装macOS

#### 1、参照[此视频](https://www.youtube.com/watch?v=u2KaYy_93QI)进行BIOS设置

#### 2、使用[GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)更改序列号

#### 3、参照[OpenCore的使用手册](https://sumingyd.github.io/OpenCore-Install-Guide/installer-guide/)，刷入镜像，制作启动盘。

#### 4、使用本EFI文件引导安装macOS

<br />

### 二、完善macOS，驱动蓝牙、解锁CFG Lock

#### 1、使用[OCLP-Mod](https://github.com/laobamac/OCLP-Mod/releases/tag/2.6.4)给Intel网卡打补丁

- 本仓库的EFI中，config.plist文件已经修改好，可以直接打补丁。

#### 2、使用[Modifed GRUB Shell](https://github.com/datasone/grub-mod-setup_var/releases)解锁CFG Lock

- ##### 具体可以参照这个教程：https://hujewelz.github.io/cko3zrglu0019h7s6drqzgue3/
- ##### [FWKTBFA](https://pcsupport.lenovo.com/us/en/products/desktops-and-all-in-ones/thinkcentre-m-series-desktops/thinkcentre-m900/downloads/ds105487-flash-bios-update-intel-b150-for-thinkcentre-m700-tiny-thinkcentre-m800-m900-m900x-tiny)版本BIOS的CFG Lock偏移量为 **0x197** 。
 > 0x3C4B9 				One Of: CFG lock, VarStoreInfo (VarOffset/VarName): **0x197**, VarStore: 0x1, QuestionId: 0x87D, Size: 1, Min: 0x0, Max 0x1, Step: 0x0 {05 91 25 01 26 01 7D 08 01 00 97 01 10 10 00 01 00}


<br />

### Q&A：为什么不用其他的EFI文件，或自己制作？

- 本人是Hackintosh方面的小白，这是我经过几个晚上辛苦摸索后成功完善的EFI。
- 我在网上找到的其他M900的EFI文件，都是在EFI引导加载完成后直接黑屏，显示器无信号（似乎是无法驱动HDMI拓展模块）。又或是无法驱动M900的NVME硬盘。

<br />

#### 以上。
