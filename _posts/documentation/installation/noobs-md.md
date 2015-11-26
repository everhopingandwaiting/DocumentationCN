---
ID: 60
post_title: NOOBS
author: 有聰哥冇甩拖
post_date: 2015-10-16 23:26:28
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/installation/noobs-md/
published: true
---
# NOOBS

**开箱即用的软件** - 树莓派的系统安装管理软件

![NOOBS OS selection](https://raw.githubusercontent.com/raspberrypi/documentation/master/installation/images/noobs.png)

## 如何获取NOOBS

### 购买预装NOOBS的SD卡

获取NOOBS最便捷的途径，绝对是购买一张预装了NOOBS的SD卡！详细请浏览<a href="http://swag.raspberrypi.org/collections/frontpage/products/noobs-8gb-sd-card" target="_blank">Swag Store</a>，只售£4！

### 下载

除此之外，<a href="https://www.raspberrypi.org/downloads/noobs/" target="_blank">树莓派官方网站的下载页面</a>上也有提供NOOBS的下载链接。

#### 如何将NOOBS安装到SD卡

下载好NOOBS的压缩包之后，需要将包内的文件复制到已格式化的SD卡上。

安装NOOBS步骤：

- 将一张至少4G的SD卡格式化为FAT，可参考下面的指引进行。
- 解压NOOBS_vX_X_X.zip（X_X_X为版本号，当前最新版本为v1.4.2）。
- 将解压好的文件复制到刚才格式化的SD卡的根目录上。请注意注意：有时可以会将解压好的文件复制到了一个文件夹，请把文件夹里面的所有文件移动到SD卡的根目录。
- 第一次启动时，刚才格式化的FAT会自动缩小到最佳的大小，然后安装指引界面会列出可供选择的操作系统。

#### 如何将SD卡格式化为FAT格式

**注意：** 对于大于32G（如64G）的SD卡的格式化，请参考另外的[SDXC格式化](../sdxc_formatting.md)指引。

##### Windows

建议Windows用户使用SD协会的格式化工具，<a href="https://www.sdcard.org/chs/downloads/formatter_4/eula_windows/index.html" target="_blank">SD Formatter （Windows版）</a>。格式化时，需要在“选项设置”中将“逻辑大小调整”设置成“开启（On）”，以确保格式化的是来整个SD卡，而不只是一个分区。

##### Mac OS

除了系统自带的OSX Disk Utility之外，Mac用户也可以使用<a href="https://www.sdcard.org/chs/downloads/formatter_4/eula_mac/index.html" target="_blank">SD Formatter（Mac版）</a>将整个SD卡格式化。选择SD卡的盘符然后以`MS-DOS`格式抹掉（Erase）。

##### Linux

建议Linux用户使用`gparted`（或命令行版本的`parted`）进行整个SD卡的格式化。另外，也可参考Norman Dunbar为Linux用户写的一个<a href="http://qdosmsq.dunbar-it.co.uk/blog/2013/06/noobs-for-raspberry-pi/" target="_blank">树莓派NOOBS指引</a>。

## NOOBS里面的东东

目前NOOBS里面可供选择的系统有：

- [Raspbian](http://raspbian.org/)
- [Pidora](http://pidora.ca/)
- [OpenELEC](http://wiki.openelec.tv/index.php?title=Raspberry_Pi_FAQ)
- [RaspBMC](http://www.raspbmc.com/)
- [RISC OS](https://www.riscosopen.org/wiki/documentation/show/Welcome%20to%20RISC%20OS%20Pi)
- [Arch Linux](http://archlinuxarm.org/platforms/armv6/raspberry-pi)

在NOOBS v1.3.10（2014年9月时的版本）中，只包含Raspbian的离线安装包，其他的系统需要连网下载。

## NOOBS和NOOBS Lite

NOOBS有两个版本：NOOBS，离线及在线安装；以及NOOBS Lite，仅限在线安装。

完整版NOOBS包含了Raspbian的离线安装包，所以安装Raspbian时树莓派无需连网；但如果安装其他系统或使用NOOBS Lite安装系统时，树莓派需要连网。

注意：使用完整版NOOBS安装的系统可能并非该发行版的最新版本，但当系统启动后，如果系统连网检测到有更新时，将会有选项供用户选择是否更新。

## NOOBS开发

### Latest NOOBS release

目前NOOBS最新版本为**v1.4.2**，发行于**2015年9月24日**；而NOOBS Lite为**v1.4**，发行于**2015年2月18日**。

(从NOOBS v1.4.0 开始, NOOBS Lite仅显示两位数的版本号，例如：v1.4)

### NOOBS文档

关于NOOBS高级配置的完整文档，托管在<a href="https://github.com/raspberrypi/noobs/blob/master/README.md" target="_blank">GitHub</a>上。

### NOOBS源代码

同时，NOOBS的源代码也托管在<a href="https://github.com/raspberrypi/noobs" target="_blank">GitHub</a>上。
