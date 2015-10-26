---
ID: 240
post_title: 音频设置
author: 有聰哥冇甩拖
post_date: 2015-10-24 01:03:52
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/configuration/audio-config-md/
published: true
---
# 音频设置

树莓派有两种音频输出模式：HDMI和耳机插孔（译者注：2代B型为3.5mm的音视频复合接口）。用户可以随时更换输出模式。

如果树莓派连接的HDMI显示器或电视机带有音箱，音频可以通过HDMI线缆传输，但也可以改为通过音频接口使用耳机或其他音箱播放。如果树莓派的显示器带有音箱，音频将会自动通过HDMI接口播放；如果显示器没有音箱，则会通过音频接口播放。如果需要更改音频输出设置，或者自动侦测结果有误，可尝试手动更改音频输出设置。

## 更改音频输出设置

更改的方法有两种

### 命令行更改

下面的命令可以改由HDMI播放音频：

`amixer cset numid=3 2`

这条命令将输出接口指定为`2`，即HDMI。若指定为`1`则选择模拟输出（耳机插孔）。默认设置为`0`，即自动。

### 使用raspi-config更改

输入以下命令，打开[raspi-config](raspi-config.md)：

`sudo raspi-config`

屏幕将显示如下画面：

![raspi-config screen](https://github.com/RaspberryPiChina/documentation/raw/master/configuration/images/raspi-config.png)

选择`Advanced Options`，然后按下`Enter`，选择A6，`Audio`，再按下`Enter`。

![Audio configuration screen](https://github.com/RaspberryPiChina/documentation/raw/master/configuration/images/raspi-config-audio.png)

然后，除了`Auto`之外，程序将会提供上述的另外两种模式供用户选择。选定后按下`Enter`，再按右箭头退出当前列表，最后选择`Finish`，退出raspi-config。

## 万一仍然无法通过HDMI播放音频

某些特殊情况下，用户需要通过修改`config.txt`强制使用HDMI模式（与之相对的选项是并不传输音频的DVI模式）。在`/boot/config.txt`中搜索`hdmi_drive`，并确保等号后的数值为`2`，保存后重启使设置生效。
