---
ID: 712
post_title: Raspbian的更新和升级
author: admin
post_date: 2015-12-16 17:17:59
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/raspbian/updating-md/
published: true
_theme_show_post_title: 0
---
# Raspbian的更新和升级

首先，用下面这条命令，将系统的软件包列表**更新**：

    sudo apt-get update

然后，用下面这条命令，将所有已安装的软件**升级**到最新版本：

    sudo apt-get upgrade

通常说来，不时执行一下这两条命令，可以系统把握时代脉搏，走在历史前沿，几乎与<a href="http://www.raspberrypi.org/downloads/" target="_blank">最新的发行版</a>一致。

但总有可能官方的镜像中会有些更新需要用户干预。对于这种情况，这两条命令不会自动应用更新。

## 更新内核和固件

内核和固件是以软件包的形式安装的，前面介绍的命令也可以升级。不过这两个东东的更新通常不会太频密，只有经过严格测试后才会发行更新包。

译者是不会告诉你这个世界上有一个程序叫rpi-update的，不过需要事先安装。安装的命令是：

    sudo apt-get install rpi-update

当需要更新的时候，输入命令：

    sudo rpi-update

注意：内核和固件的更新可能会出现不可预料的错误，请自行承担更新内核和固件可能面临的所有风险。

## 空间不足

执行`sudo apt-get upgrade`这条命令的时候，程序会提示需要多少SD卡的空间。如果不清楚剩余多少空间，最好事先执行`df -h`检查一下，因为`apt`不会自动帮你做这个任务。另外，下载的软件包（`.deb`文件）是保存在`/var/cache/apt/archives`的，如果需要删除，可以执行`sudo apt-get clean`。
