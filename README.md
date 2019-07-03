># Asrock-Z370m-Pro4-Hackintosh

## 硬件

>CPU：Intel i5 8500

>主板：Asrock z370m Pro4

>显卡：蓝宝石RX580 8G D5 超白金极光特别版

>显示器：LG 27UK600 （3840x2160）DP接口

>Wi-Fi 和蓝牙：BCM94360CD （Wi-Fi插上就能用，蓝牙需要打移除USB限制补丁）

>内存：金士顿掠食者 8G DDR4 3200Mhz x 2

>硬盘：闪迪至尊超极速480G SSD


## 系统概况

>系统版本：macOS Mojave 10.14.5

>机型：iMac19,2

>更新的config.plist是有效的，其他文件参考请下载黑果小兵的10.14.5安装镜像。

>主要使用到的kext为：USBInjectAll.kext Lilu.kext AppleALC.kext WhateverGreen.kext 已经包含几乎所有显卡音频usb的驱动，
                 其他kext请参考‘文件说明.pdf‘

>各功能情况（95%+）：CPU、核显、独显、Wi-Fi、蓝牙、睡眠及唤醒、声音、USB都基本正常，config.plist已经上传。

>该项目主要参考Houcoder的部分USB部分设定，其他的针对我的配置从黑果小兵的默认配置上进行修改，仅供参考，不要盲目使用。

## 升级记录

| 版本 | 日期 | 备注 |
|-------------------------------|-----------|----------|
| macOS Mojave 10.14.4 (18E226) | 2019.4.28 | 正常，无异常 |
| macOS Mojave 10.14.5 (18F132) | 2019.5.20 | 正常，无异常 |


## BIOS 设置

>BIOS 版本：3.20

>Advanced \ Chipset Configuration → Vt-d : Disabled （仅安装时）

>Advanced \ Super IO Configuration → Serial Port: Disabled（仅安装时）

>Advanced \ USB Configuration → XHCI Hand-off : Enabled

>Advanced \ Chipset Configuration → Share Memory : 128MB or Auto

>Advanced \ Chipset Configuration → IGPU Multi-Monitor : Enabled

## 安装注意事项

### 音频

为了让音频正常工作，板载ALC892的Audio Inject 的值为 `1`。

**移除 USB 端口限制**（config里面已经集成补丁）
安装完 macOS 10.14.4 后需要移除 USB 端口限制，如果不移除你只能在 FB Patcher 上看到 15 个 USB 端口。移除方法请参考 [List of Hackintosh USB Port Limit Patches (10.14 Updated)](https://hackintosher.com/forums/thread/list-of-hackintosh-usb-port-limit-patches-10-14-updated.467/)。


## 已知的一些问题

### 睡眠后小概率出现蓝牙不可用的情况

>这个问题在白苹上也有，遇到这种问题重启下蓝牙服务即可：`` $ sudo kill -9 `pgrep bluetoothd` `` - [Restart Bluetooth Daemon on Mac OS X without restarting](https://gist.github.com/nicolasembleton/afc19940da26716f8e90#gistcomment-2636787)。

## USB 端口映射关系

>HSXX 代表的是 USB 2.0，SSXX 代表的是 USB 3.0。

>主板背部：

![port mapping](./images/motherboard-usb-mapping.png)

>蓝牙：HS05

>机箱前置 USB（上）：HS09 SS06

>机箱前置 USB（下）：HS10 SS05

