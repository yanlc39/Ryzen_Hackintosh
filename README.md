# Ryzen_Hackintosh
## OpenCore EFI for AMD Ryzen Hackintosh(Ryzen 5 2600 + BIOSTAR X370GTN)

## Specification
| **Component** | **Model** |
| ------------- | --------- |
| CPU | AMD Ryzen 7 2600 @ 3.8GHz |
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

  3. 通过 [**GenSMBIOS**](https://github.com/corpnewt/GenSMBIOS) 获得3码认证，以激活`iMessage`、`Facetime`等功能

  4. 通过[**ProperTree**](https://github.com/corpnewt/ProperTree)打开`OC`目录下的`config.plist`，填入相应的`MLB`、`Sereial`和`SmUUID`

  5. 通过[**gibMacOS**](https://github.com/corpnewt/gibMacOS/)制作您的原版MacOS镜像恢复盘

  6. 在BIOS中设置为U盘启动，即可开始 

**你不能使用本样例中的三码, 每一台Hackintosh都需要独立的三码，且本例中的三码为空**