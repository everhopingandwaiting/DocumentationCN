---
ID: 279
post_title: 摄像头设置
author: adm
post_date: 2015-10-25 12:06:57
post_excerpt: ""
layout: post
permalink: >
  https://www.rpicn.org/documentation/configuration/camera-md/
published: true
---
# 摄像头设置

## 硬件设置

**警告：**摄像头对静电敏感，触摸摄像头模块之前请务必充分接地放电。如果没有接地铜织带，可以尝试触摸片刻水龙头充分放电。

摄像头模块通过一组15针的排线连接树莓派。排线一端接摄像头，另一端接树莓派。排线需要正确连接，摄像头方可正常工作。在摄像头这端，排线蓝色漆面应背离电路板；而在树莓派这端，排线的蓝色漆面应向着以太网线接口（1代A型则应该向着3.5mm音频接口）。

虽然排线接口在摄像头和树莓派上有所不同，但它们安装方法一样。在树莓派上，拉起接头两端的卡扣，将排线插到接口尽头，确认排线竖直插进接口，然后用暗力按下两边卡扣卡稳排线。在摄像头上，同样需要拉起卡扣，将排线插到尽头，再用暗力按下卡扣。因为体积更小的关系，摄像头一端可能比树莓派一端更难操作。

## 设置摄像头软件

首先连接互联网，再输入以下命令更新软件：

    sudo apt-get update
    sudo apt-get upgrade

使用`raspi-config`程序启用摄像头模块：

    sudo raspi-config

使用上下方向键移到摄像头选项，再选择启用。在退出`raspi-config`时，程序会提示建议重启。重启后树莓派会应用相应的设置，并且将为GPU分配足够的内存，保证摄像头有足够资源正常运行。

下面的命令可以测试摄像头的是否正常工作：

    raspistill -v -o test.jpg

如果摄像头正常工作，显示器将显示五秒的影像预览后拍摄照片，保存为test.jpg，同时也会显示其他的一些信息。

## 故障处理

参考[摄像头故障处理](../../troubleshooting/hardware-troubleshooting/camera.md)。
