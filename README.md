# asrock-z370m-pro4-hackintosh

[English version](./README-EN.md)

该项目只针对我的配置，仅供参考，不要盲目使用。

## 硬件

CPU：Intel i5 8500

主板：[Asrock z370m Pro4](https://www.asrock.com/MB/Intel/Z370M%20Pro4/index.asp)

显卡：[蓝宝石RX580 8G D5 极光版 ](http://www.sapphiretech.com/productdetial.asp?pid=C12A4F7E-B791-4DDB-8D32-47BB6ACA68BD&lang=chs)

Wi-Fi 和蓝牙：BCM94360CD

内存：金士顿 8G DDR4 3200Mhz x 2

硬盘：闪迪至尊超极速480G SSD

Wi-Fi插上就能用，蓝牙需要打USB限制补丁。

## BIOS 设置

BIOS 版本：3.20

Advanced \ Chipset Configuration → Vt-d : Disabled

Advanced \ Super IO Configuration → Serial Port: Disabled

Advanced \ USB Configuration → XHCI Hand-off : Enabled

Advanced \ Chipset Configuration → Share Memory : 128MB

Advanced \ Chipset Configuration → IGPU Multi-Monitor : Enabled

## 安装注意事项

### 音频

为了让音频正常工作，板载ALC892的Audio Inject 的值为 `1`。

### 让 USB 顺利工作

USB 不正常工作的表现有：

1. USB 不能识别。
2. 睡眠后会立即醒来。
3. USB 3.0 的速度会限制在 480 Mbps。
4. 重启后 USB 设备丢失，需要重新插拔。


**1 移除 USB 端口限制**

安装完 macOS 10.14.4 后需要移除 USB 端口限制，如果不移除你只能在 FB Patcher 上看到 15 个 USB 端口。移除方法请参考 [List of Hackintosh USB Port Limit Patches (10.14 Updated)](https://hackintosher.com/forums/thread/list-of-hackintosh-usb-port-limit-patches-10-14-updated.467/)。

**2 使用 FB Patcher 制作 USB 补丁**

安装完上面的补丁后重启电脑应该可以看到所有的 USB 接口了，按照 [USB Port Patching](https://www.tonymacx86.com/threads/release-intel-fb-patcher-v1-6-5.254559/) 的教程来制作属于你自己的 USB 补丁。

**3 保存好制作的补丁**

补丁制作完成后一定要好好保存，因为是针对自己电脑独有的文件，网上找不到第二份。

### Intel Framebuffer Patching

为了让集成的 Intel UHD 630 显卡正常的工作，需要做 Framebuffer Patching，具体步骤参考这个文档 - [Intel Framebuffer patching using WhateverGreen](https://www.insanelymac.com/forum/topic/334899-intel-framebuffer-patching-using-whatevergreen/)。

文章很长，很难懂，8 代 CPU 直接看这里即可：[corpnewt/Hackintosh-Guide](https://github.com/corpnewt/Hackintosh-Guide/blob/master/config.plist-per-hardware/coffee-lake.md#properties)。

## 已知的一些问题

### 睡眠后小概率出现蓝牙不可用的情况

这个问题在白苹上也有，遇到这种问题重启下蓝牙服务即可：`` $ sudo kill -9 `pgrep bluetoothd` `` - [Restart Bluetooth Daemon on Mac OS X without restarting](https://gist.github.com/nicolasembleton/afc19940da26716f8e90#gistcomment-2636787)。

## 升级系统怎么办？

不要第一时间升级，新系统推送后过两周去社区看看问题反馈。决定升级前备份好系统，即使升级失败也能回滚到历史版本。

## USB 端口映射关系

HSXX 代表的是 USB 2.0，SSXX 代表的是 USB 3.0。

主板背部：

![port mapping](./images/motherboard-usb-mapping.png)

蓝牙：HS05

机箱前置 USB（上）：HS09 SS06

机箱前置 USB（下）：HS10 SS05

## 升级记录

| 版本 | 日期 | 备注 |
|-------------------------------|-----------|----------|
| macOS Mojave 10.14.2 (18C54)  | 2018.12.7 | 正常升级，无异常 |
| macOS Mojave 10.14.3 (18D42)  | 2019.1.23 | 正常升级，无异常 |
| macOS Mojave 10.14.3 (18D109) | 2019.2.11 | 正常升级，无异常 |
| macOS Mojave 10.14.4 (18E226) | 2019.3.26 | 正常升级，无异常 |

## 跑分测试

### Geekbench CPU

<img src="./images/geekbench-cpu.png" alt="geekbench-cpu-score" width="400px">

### Geekbench GPU

<img src="./images/geekbench-gpu-opengl.png" alt="geekbench-gpu-opengl-score" width="400px">

### Cinebench

<img src="./images/cinebench.png" alt="cinebench-score">

## 参考链接

1. [如何正确的黑苹果](https://catty-house.blogspot.com/2018/10/hackintosh.html)
1. [Kernel panic in Safari with UHD 630 + RX 570](https://www.tonymacx86.com/threads/kernel-panic-in-safari-with-uhd-630-rx-570.264222/)
1. [正确驱动Intel显卡的Framebuffer](https://catty-house.blogspot.com/2018/10/intelframebuffer.html)
