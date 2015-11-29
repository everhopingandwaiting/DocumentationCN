---
ID: 679
post_title: >
  树莓派精推荐简优化系统——DietPi介绍
author: 思兼
post_date: 2015-11-29 14:56:44
post_excerpt: ""
layout: post
permalink: >
  https://www.rpicn.org/sjqlwy/%e6%a0%91%e8%8e%93%e6%b4%be%e7%b2%be%e6%8e%a8%e8%8d%90%e7%ae%80%e4%bc%98%e5%8c%96%e7%b3%bb%e7%bb%9f-dietpi%e4%bb%8b%e7%bb%8d/
published: true
---
简介：DietPi是一个非常棒的树莓派操作系统，在官方推荐系统Raspbian基础上进行了大量精简优化，支持所有型号的Raspberry Pi (暂不支持计算模块)，Odroid-C1，Odroid-XU3/4，Orange Pi (测试版)以及Vmware虚拟机。可以方便快捷地安装大量常见软件(如LASP，Kodi，Wordpress,OpenVPN等)，同时进行了非常多的优化。 官方主页：<http://dietpi.com/> 项目主页：<https://github.com/Fourdee/DietPi> 项目主贴：<https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=100976> 更新说明：<https://github.com/Fourdee/DietPi/blob/master/CHANGELOG.txt> 下载地址：<http://fuzon.co.uk/phpbb/viewtopic.php?f=8&t=9#p9>【当前最新版本：<http://dietpi.com/downloads/DietPi_RPi-(Jessie).7z> 】 DietPi的特点与使用心得： 1.支持所有树莓派型号(暂不支持计算模块)，大量精简优化，如减少读写，延长SD卡寿命 2.可以通过DietPi-Software简单快捷地安装大量常用软件，抛弃繁琐配置，不用费神编译源码敲命令 3.DietPi-Config功能丰富，可对超频，日志记录，无线网络连接等进行设置 4.体积小 比起Raspbian 2G多的体积，DietPi下载镜像只有不到100MB (V100) 5.需求低 比ArchLinux arm安装后占用的空间还小，仅作服务器使用的话1G大小的SD卡也可以 6.身轻如燕、健步如飞 启动后进程少，内存占用低 7.Wifi功能支持完善 8.比Raspbian拥有更小的体积，更多的功能 9.更新非常频繁！每次都有新功能加入！半年不到版本号已经从v34飙到v100 10.最新版升级到Jessie，带来了systemd作为系统服务管理器，网络上很多设置开机启动的教程基于init系统，也就是修改rc.local之类的。如果不习惯可以先下载Wheezy版。 DietPi核心功能一览： DietPi-Software：可以方便快捷地安装流行软件，无需繁琐设置，"开箱即用"。详细支持软件列表请移步：<http://dwz.cn/2b0jqF> DietPi-Config：设备软硬件参数调整工具，拥有比官方raspi-config更多的选项。 DietPi-Backup：备份系统从此变得简单！不需要dd和win32diskimager~ DietPi-Sync：目录同步，随心所欲 DietPi-Nice：调整已安装软件的运行优先级(初级玩家慎用) Logging System Choices：可以根据自己的需求改变日志记录水平，想要更安全还是更快速？(初级建议使用默认设置，Ramlog可以减少SD卡读写以延长其寿命) File Server Choices：方便地将树莓派变成一台文件服务器，可以选择功能丰富设置简单的Samba或是更少CPU占用的Proftpd。 DietPi-Update System：联网时Dietpi可以自动检测更新并通过简单的命令完成系统更新而不用重新烧写镜像 Wifi Support：不像其他一些小体积的发行版(如Arch Linux等)，DietPi拥有完整的Wifi支持，无需手动安装软件，并可以方便地连接到无线网络。 关于DietPi的博客介绍： 我自己写的两篇，有些内容已经过时：<http://www.cnblogs.com/sjqlwy/p/4446071.html> <http://www.cnblogs.com/sjqlwy/p/4457006.html> 已支持软件列表(部分)： LXDE 桌面环境 Kodi 多媒体中心 MiniDLNA 流媒体服务器 Transmission & Deluge BT下载 [DietPi-Cam][1] 简单易用的树莓派摄像头网页控制前端，支持诸多功能，最主要是即插即用，一键安装啊！ OwnCloud 私有云存储服务 WordPress 流行的博客平台 Weaved 之前介绍过的物联网服务，支持内网穿透 WebIOPi 通过网页前端控制树莓派的GPIO接口 Linux Dash & PhpSysInfo 监控运行状态的网页前端 LAMP&phpMyAdmin等 Web服务器，一键安装！！ OpenVPN & SoftEther VPN服务器 NoIP 类似花生壳一类的DDNS服务

 [1]: 树莓派wiki--硬件--摄像头--网络控制--RPi-Cam-Web-Interface.html