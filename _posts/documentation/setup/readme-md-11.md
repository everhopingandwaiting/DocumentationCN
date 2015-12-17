---
ID: 32
post_title: 树莓派安装
author: adm
post_date: 2015-10-16 11:21:45
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/setup/readme-md-11/
published: true
_theme_show_post_title: 0
---
# 树莓派安装

树莓派安装向导

## 需要的配件

### 必备品（日常使用）

- [SD卡（TF卡）](../installation/sd-cards.md)
    - 建议使用8G的C4或以上的SD卡（TF卡），最好事先准备好[NOOBS](../installation/noobs.md)；
- [显示设备和接口](monitor-connection.md)
    - 一般情况下，支持HDMI或DVI的电视或显示器都可与树莓派一起使用。为保证最佳效果，请使用有HDMI输入的显示设备；另外支持旧式显示设备的接口同样可用。
- 键盘和鼠标
    - 标准的USB键盘和鼠标都适用于树莓派。
    - 已成功配对的无线键盘和鼠标也可使用。
    - 键盘布局设置，请参考[raspi-config](../configuration/raspi-config.md)。
- [电源](../hardware/raspberrypi/power/README.md.12)
    - 树莓派使用Micro USB接口连接电源（与大多数的移动电话一样）。
    - 电源的最低要求：5V-0.7A。（目前树莓派2代B型的建议是5V-2A）。
    - 低功率电源（小于0.7A）也可能提供树莓派的基本需求，但万一供电需求不足时将可能导致树莓派重启。

### 可选设置

- 以太网线 [仅限Model B/B+/2B]
    - 使用网线可令树莓派连接互联网。
- [USB无线网卡](../configuration/wireless/README.md.13)
    - 除了使用网线之外，也可使用无线网卡连接互联网，但需要另作配置。	
- 音频线
    - 音频可以通过3.5mm插孔使用音箱或耳机播放。
    - 如果没有HDMI线，则需要音频线播放音频。
    - 如果已使用HDMI连接到了带音箱的显示器，则无需另接音频线，因为音频可由显示器直接播放。但如果需要另外的音箱播放音频，也可以同时再另接音频线（需要另行[设置](../configuration/audio-config.md)）。

## 故障处理

在设置过程中遇到任何问题，请参考[故障处理](../troubleshooting/README.md.10)。
