# Ryzen_Hackintosh
## OpenCore EFI for AMD Ryzen Hackintosh(Ryzen 5 2600 + BIOSTAR X370GTN)

## Specification
| **Component** | **Model** |
| ------------- | --------- |
| CPU | AMD Ryzen 5 2600 @ 3.8GHz |
| Motherboard | BIOSTAR X370GTN |
| RAM | 16GB (2 x 8GB) 威刚 @ 2800MHz |
| Audio Chipset | ALC-892 |
| GPU | XFX RX470D 4GB |
| Ethernet | RealtekRTL8111 |
| OS Disk (SSD) | Samsung SSD 128G |

**macOS version**: 10.15.5 (19F2200) 
**OpenCore version**: 0.5.9  

## Drivers & Kexts
 - [[Bootloader] OpenCore](https://github.com/acidanthera/OpenCorePkg)
 - [[Patch] AMD_Vanilla](https://github.com/AMD-OSX/AMD_Vanilla)
 - [[Driver] OpenRuntime](https://github.com/acidanthera/OpenCorePkg)
 - [[Driver] HFSPlus](https://github.com/acidanthera/OcBinaryData/blob/master/Drivers/HfsPlus.efi)
 - [[Kext] Lilu](https://github.com/acidanthera/Lilu)
 - [[Kext] VirtualSMC](https://github.com/acidanthera/VirtualSMC)
 - [[Kext] WhateverGreen](https://github.com/acidanthera/WhateverGreen)
 - [[Kext] AppleALC](https://github.com/acidanthera/AppleALC)
 - [[Kext] RealtekRTL8111](https://bitbucket.org/RehabMan/os-x-realtek-network/downloads/)

## Not working
 - 虚拟机失效(XCode iOS emulator正常，但Android Studio不可用)
 - 未找到正确的LayOut-ID，故麦克风不可用，扬声器正常
 - 无法睡眠(睡眠后无法唤醒)

## How to use
  1. 将`EFI`文件夹克隆到本地

     > ​	git clone https://github.com/yanlc39/Ryzen_Hackintosh.git

  2. 将`EFI`文件夹中的`OC`与`BOOT`放入引导磁盘中

  3. 通过[**GenSMBIOS**](https://github.com/corpnewt/GenSMBIOS)获得3码认证，以激活`iMessage`、`Facetime`等功能

  4. 通过[**ProperTree**](https://github.com/corpnewt/ProperTree)打开`OC`目录下的`config.plist`，填入相应的`MLB`、`Sereial`和`SmUUID`

  5. 通过[**gibMacOS**](https://github.com/corpnewt/gibMacOS/)制作您的原版MacOS镜像恢复盘

  6. 在BIOS中设置为U盘启动，即可开始 

**你不能使用本样例中的三码, 每一台Hackintosh都需要独立的三码，且本例中的三码为空**

## Why OpenCore

1. 从 2019 年 9 月以后, Acidanthera 开发的内核驱动 (Lilu, AppleALC 等等) **「不再会」** 在 Clover 上做兼容性测试
2. OpenCore 更加注重系统的安全性, 提供对 OpenCore 自身引导文件对加密, 同时对文件保险箱 (FileVault) 有更强大的支持, 在未来会支持 UEFI 安全启动
3. OpenCore 启动 FileVault (硬盘保险箱) 加密的分区速度远超 Clover
4. OpenCore 支持基于 `boot.efi` 的原生开机快捷键支持
5. OpenCore 使用更加先进的方法注入第三方内核扩展驱动 (Kext) 且与此同时不会破坏系统完整性保护
6. OpenCore 通过读取启动磁盘设置的 NVRAM 变量, 可以像白苹果一样支持在设置的启动磁盘切换默认引导项
7. 支持给其它 .efi 驱动或引导工具加入参数
8. 大量 Acidanthera 维护的独立 UEFI 驱动被合并入 OpenCore, 未来的开发直接与 OpenCore 绑定, **且不再支持 Clover**
9. **无痛进行MacOS的系统更新，与白苹果更新系统有相同体验**

## Attention
#### 你应该关闭的BIOS选项
| **英文** | **中文** |
| ------------- | --------- |
| Fast Boot | 快速启动 |
| CFG Lock(MSR 0xE2 write protection) | CFG 锁 (MSR 0xE2 写入保护) |
| CSM | 兼容性支持模块 |

#### 你应该开启的BIOS选项
| **英文** | **中文** |
| ------------- | --------- |
| SVM | SVM |
| Above 4G decoding | 大于 4G 地址空间解码 |
| EHCI/XHCI Hand-off | 接手 EHCI/XHCI 控制 |
| Hyper Threading | 处理器超线程 |
| OS type: Windows 8.1/10 | 操作系统类型: Windows 8.1/10 |

#### 你应该阅读的内容

1. [OpenCore](https://github.com/acidanthera/OpenCorePkg/blob/master/Docs/Configuration.pdf)**官方**文档说明
2. [AMD-OSX](https://forum.amd-osx.com/index.php)
3. 基于[Ryzen and Threadripper](https://dortania.github.io/OpenCore-Desktop-Guide/AMD/zen.html)的设置向导

#### 你需要的有

1. 耐心。没有耐心将无法体验`Hackintosh`带来的乐趣
2. 求知的心。有些问题将是你一人无法解决的，请提出你遇到的问题
3. 一台能够正常使用的计算机，以防不测
4. **解决问题，需要努力的是自己，不是让别人帮你努力；帮你解答是情分，不是义务**