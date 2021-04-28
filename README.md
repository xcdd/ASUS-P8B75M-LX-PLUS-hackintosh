
## **ASUS-P8B75M-LX-PLUS-hackintosh**

使用opencore0.6.8构建

**U** 盘安装的同学，请使用 ****USB2.0**** 完成安装，别着急联网，先用 ****OpenCore Configurator**** （或者别的工具也行）刷新三码，不刷新就联网的后果自负 ...

![](https://github.com/xcdd/asus-p8b75m-hackintosh/blob/main/picture/image.png)

## **本机配置**

| CPU | E3-1240 |
| --- | --- |
| 主板 | 华硕P8B75-M LX PLUS BIOS版本 2.10.1208 / BIOS日期: 04/25/2013 |
| 内存 | 两条深圳产杂牌内存（4+8=12GB） |
| 主硬盘 | 金士顿A400（500G，SATA）大号U盘，别买 |
| 核心显卡 | 无 |
| 独立显卡 | colorfire（镭风）网锋 HD7850-GD5 2G BA1 |
| 有线网卡 | Realtek小螃蟹千兆内置卡 |
| 声卡 | ALC887 （Layoutid=1） |
| 备注 | 另加了一块PCIE的USB3.0扩展卡，好久之前买的，居然也可以免驱黑苹果，型号不知，芯片是VIA的VL805 |

![](https://github.com/xcdd/asus-p8b75m-hackintosh/blob/main/picture/Luban_161959580424632e6c949-10f2-4651-af2e-ad46e9648540.jpeg)

提示：

1. 4代以前的CPU核显驱动不了bigsur，因为苹果对其的原生支持到10.13.6版本为止，本引导并未测试过与10.13.6的兼容性，而且我这是E3，没有核显~
> 有一些办法可以让老核显用上新系统的，但很麻烦并且我未成功过

2. 本显卡是镭风显卡1GB显存的版本（网锋 HD7850-GD5 2G BA1），原生不支持UEFI，我通过改显卡BIOS实现支持，显卡BIOS在这里（使用风险自担）：
> 不支持UEFI的显卡在主板里没办法关闭CSM，可能存在兼容性问题
 
## BIOS 配置

请在高级模式（advanced mode）下配置

### **高级页面**

处理器设置-开启超线程、Intel虚拟技术

南桥-关闭intel快速启动、intel智能连接

**SATA**** 设置 ****-SATA**** 模式选择： ****AHCI**** （默认的 ****IDE**** 模式肯定是装不上的，必须改）**

北桥-内存重寻址功能（above 4g）：开启

USB设置-intel xhci 模式：开启，USB2.0 ehci不关也没事

高级电源管理（APM）：全部关闭，因为本引导未设置休眠


### **启动页面**

快速启动：关闭

开机画面：FULL SCREEN

CSM：关闭（如果显卡BIOS不支持UEFI则无法关闭）

启动选项：选择OC引导所在的位置，此主板可以自动识别不用添加UEFI启动项

## **目前工作情况**
测试在big sur 11.3/11.2.3正常运行

CPU变频正常 显卡识别成马甲卡，不影响使用（如不用whatevergreen.kext可解决此问题）

暂未完善休眠，当前使用8811CU芯片的USB无线网卡

![](https://github.com/xcdd/asus-p8b75m-hackintosh/blob/main/picture/c54588af-2239-4494-93ee-f84c08b8a44c.png)
![](https://github.com/xcdd/asus-p8b75m-hackintosh/blob/main/picture/1bedd7d3-0e3d-4790-b1fb-3d92baf2902d.png)
