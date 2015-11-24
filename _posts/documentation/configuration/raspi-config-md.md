---
ID: 132
post_title: raspi-config
author: 有聰哥冇甩拖
post_date: 2015-10-19 23:54:55
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/configuration/raspi-config-md/
published: true
---
# raspi-config

`raspi-config`是由[Alex Bradbury](https://github.com/asb)编写并维护的树莓派设置工具，特别为Raspbian度身订造。

## 用法

第一次运行Raspbian时，系统会提醒用户运行`raspi-config`。要开始使用这个工具，只需要在终端输入这个命令：

    sudo raspi-config

`sudo`意思是临时以超级用户执行后面的命令，因当前用户`pi`可能不具备修改一些特别文件的权限。

随后终端将显示一个蓝色的屏幕，还有一个列满各种选项的灰色框框，如下图所示：

![raspi-config main screen](https://github.com/raspberrypi/documentation/blob/master/configuration/images/raspi-config.png)

工具提供的选项包括：

`                        Raspberry Pi Software Configuration Tool (raspi-config)`
` `
`Setup Options`
` `
`    1 Expand Filesystem              Ensures that all of the SD card storage is available to the OS`
`    2 Change User Password           Change password for the default user (pi)`
`    3 Enable Boot to Desktop/Scratch Choose whether to boot into a desktop environment, Scratch, or the command line`
`    4 Internationalisation Options   Set up language and regional settings to match your location`
`    5 Enable Camera                  Enable this Pi to work with the Raspberry Pi Camera`
`    6 Add to Rastrack                Add this Pi to the online Raspberry Pi Map (Rastrack)`
`    7 Overclock                      Configure overclocking for your Pi`
`    8 Advanced Options               Configure advanced settings`
`    9 About raspi-config           Information about this configuration tool`
` `
`                                   <Select>                                  <Finish>`

### 在菜单中移动光标

在各个选项中，可以使用上下箭头键高亮显示各种选项。按下右箭头会跳到“选择”和“完成”按钮，按下左箭头则返回选项列表。此外，还可以使用“Tab”键切换这两个区域。

另外值得一提的是，假如选项列表非常长，比如“时区”列表，用户可以按字母键快速跳到相应的部分。例如，按下“S”键，列表将显示以“S”开头的第一个选项“Sakhalin”，距离“Shanghai”只有几行，大大节省用户滚动列表的时间。

### `raspi-config`的任务是什么

`raspi-config`程序为常用设置的更改提供了便捷的途径。这个工具可能会更改`/boot/config.txt`或其他不同的Linux设置文件。有些选项可能需要重启方能生效，假如用户作了需要重启的改动，按下“完成”键退出`raspi-config`后，程序会提示询问用户是否重启。

## 菜单选项

###扩展文件系统（Expand filesystem）

如果Raspbian是使用NOOBS安装的，这个选项可以跳过，因NOOBS会自动扩展文件系统。但是如果用户自行使用系统镜像安装系统，则需要应用该选项，因为SD卡的系统分区会剩下3G左右未使用的空间。应用该选项后重启后生效，SD卡剩余的空间将可以全部使用。注意，该选项应用时并不需要确认，将会即时执行文件系统的扩展。

###更改用户密码（Change user password）

树莓派默认用户是`pi`，其密码是`raspberry`。在这里可以更改用户密码。参考[用户](../linux/usage/users.md)可了解更多关于用户的设置。

### 开机自动进入图形界面（Enable boot to desktop or Scratch）

树莓派开机后进入命令行界面、图形界面抑或直接到Scratch，可以在这里更改。

###区域和语言（Internationalisation options）

选中`Internationalisation options`后按回车，将进入下级菜单，可供选择的选项有：

#### 更改文字编码（Change locale）

选择一个地点，更改文字编码，简体中文为`zh_CN.UTF-8 UTF-8`。（译者注，选择了中文后，在桌面图形界面下使用终端，有时可能会出现错误）。

#### 更改时区（Change timezone）

选择合适的时区，先从大洲开始，如`Asia`，然后选择城市，例如`Shanghai`，按下空白键选中，最后按回车确认。

#### 更改键盘布局（Change keyboard layout）

更改键盘布局可能需要稍长的时间，因为加载布局列表较为费时。更改是即时生效的，但是可能需要重启。（译者注：使用中文的用户，如果键盘不是特制的话，可能可以跳过这个选项。）

### 启用摄像头模块（Enable camera）

该选项可开启摄像头模块的使用。选择`Enable`后，系统会自动为GPU分配最少128M的专用内存。

### 加入[Rastrack](http://rastrack.co.uk/)（Add to [Rastrack](http://rastrack.co.uk/)）

[Rastrack](http://rastrack.co.uk/)是基于Google Map的用户分布地图，由树莓派用户提供自己地理位置，不同颜色指示着不同的用户热度。[Rastrack](http://rastrack.co.uk/)由树莓派爱好者[Ryan Walmsley](http://ryanteck.uk/)于2012年建立。

使用这个选项便可与其他树莓派爱好者分享你的地理位置。

### 超频（Overclock）

树莓派的CPU可以超频工作，默认的主频是700MHz，可以超频到1000MHz。主频具体可以超频到什么频率可能会有不同，但超频太高可能会引致系统不稳定。选择超频时程序会提示：

```
请知悉超频可能使树莓派缩短使用寿命。如果超频导致系统不稳定，请尝试降低主频。在系统启动时按下`Shift`键可暂时禁用超频。
```

### 高级选项（Advanced options）

#### 过扫描（Overscan）

旧式电视机有着多种不同的画面尺寸，有些外壳甚至会遮挡着屏幕的一部分，因此电视机的画面尺寸只得作相应的调整，这就是“过扫描”。现在市面上的电视机或显示器一般不再需要作这样的调整，如果开机画面显示不全，请尝试启用过扫描作显示画幅的调整。

设置的改动将会在重启后生效。更详细的设置，可以直接编辑[config.txt](config-txt.md)。

一般的显示器，禁用了过扫描后，可使显示画面充满整个屏幕并自动校正。但是有部分显示器需要启用过扫描后再作微调。

#### 主机名（Hostname）

设置树莓派的在网络上的主机名。

#### 内存分割（Memory split）

更改分配给GPU的内存。

#### SSH

启用或禁用SSH客户端从远端登录树莓派。

SSH协议允许用户在另一台电脑上远程登录到树莓派的命令行界面。禁用SSH可确保SSH服务不随着树莓派开机而启动，从而节省更多资源。更多细节请参考[SSH](../remote-access/ssh/README.md)。注意：SSH默认是已启用的，如果树莓派连接到公共网络，SSH应该被禁用，除非树莓派各个用户都有密码保护。

#### 设备树

启用或禁用设备树。更多细节请参考[设备树](device-tree.md)。

#### SPI

启用或禁用SPI接口及自动加载SPI内核模块，需要其他外设产品，如PiFace。

#### I2C

启用或禁用I2C接口及自动加载I2C内核模块。

#### 串口（Serial）

启用或禁用串口通讯。

#### 音频（Audio）

设置通过HDMI或3.5mm插孔播放音频。更多细节请参考[音频设置](audio-config.md).

#### 更新（Update）

将本程序更新到最新版本。

### 关于raspi-config（About raspi-config）

选择该选项后，程序将会显示：

```
本程序为树莓派的基本设置提供直观便捷的方法。尽管本程序可随时运行，但如果系统经过深度自定义后，某些选项可能难以再次更改。
```

### 完成（Finish）

所有的设置更改后可以按下此按钮。程序会提示询问是否重启，第一次运行最好重启，以便令新设置生效。如果选择过“扩展文件系统”，重启可能会需要更长的时间。

## 开发本程序（Development of this tool）

本程序的源代码托管在[github.com/asb/raspi-config](https://github.com/asb/raspi-config)，如遇到任何问题请在GitHub上提交，也欢迎改进后提出Pull请求。

---

*注：本文参考了eLinux的文章[RPi raspi-config](http://elinux.org/Rpi_raspi-config)，其许可证为：[Creative Commons Attribution-ShareAlike 3.0 Unported license](http://creativecommons.org/licenses/by-sa/3.0/)。*
