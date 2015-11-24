---
ID: 222
post_title: 使用命令行设置Wi-Fi
author: adm
post_date: 2015-10-23 18:15:22
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/configuration/wireless/wireless-cli-md/
published: true
---
# 使用命令行设置Wi-Fi

如果不使用图形界面设置无线网络，使用这个方法就最合适不过了。哪怕树莓派没连接显示器，甚至没连接以太网，只要有串口连接也可以设置无线网络。另外值得一提的是，这个方法无需额外的软件，因为树莓派已预装所需要的工具。

## 获取无线网络信息

输入命令`sudo iwlist wlan0 scan`就可以扫描无线网络了。输入后系统将返回所有可见的无线网络列表，还包括其他有用的信息。请查找：

1. `ESSID:"testing"`。这个是无线网络的名称。
2. `IE: IEEE 802.11i/WPA2 Version 1`。这是密码验证的方式；这个例子中的验证方式是WPA2，是WPA1的升级版本，更先进更安全。本文介绍的方法适合WPA或WPA2，但可能不适合WPA2企业版；另外，WEP密码验证方式，请参考[这个网页](http://netbsd.gw.com/cgi-bin/man-cgi?wpa_supplicant.conf+5+NetBSD-current)的最后一个例子。
另外，还需要无线网络的密码，大多数的家用路由器铭牌中印有默认的无线密码。本文假设无线网络的ESSID(ssid)是`testing`，密码(psk)是`testingPassword`。

## 为树莓派添加无线网络

使用nano编辑器打开`wpa-supplicant`的设置文件：

    sudo nano /etc/wpa_supplicant/wpa_supplicant.conf

在最后一行后添加下面的代码：

    network={
        ssid="The_ESSID_from_earlier"
        psk="Your_wifi_password"
    }

对应本文的例子，就是：

    network={
        ssid="testing"
        psk="testingPassword"
    }

保存文件，按下**`Ctrl+X`**，再按**`Y`**，最后按下**`Enter`**。

这时，`wpa-supplicant`会在几秒钟内自动侦测到设置有改动，然后尝试连接无线网络。如果没有，可以尝试先输入`sudo ifdown wlan0`，然后再输入`sudo ifup wlan0`，又或者输入`sudo reboot`重启树莓派。

检测是否已连接上无线网络的方法是：输入命令`ifconfig wlan0`，然后查看`inet addr`字段是否有IP地址，如果有，说明已经成功连接无线网络；如果没有，请检查确认ESSID和密码的输入是否正确。
