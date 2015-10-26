---
ID: 423
post_title: Windows
author: 有聰哥冇甩拖
post_date: 2015-10-26 22:26:30
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/installation/installing-images/windows-md/
published: true
---
# 在Windows系统中烧写系统镜像

- 把SD卡插入读卡器并检查分配到的盘符。在“这台电脑”中，在“可移动储存器”中很容易就可能找到盘符（比如`G:`）。如果手提电脑中有SD卡槽可以将SD卡（TF卡插进SD卡套后）插进卡槽，或者使用一个优质的USB读卡器。

- 下载[Win32DiskImager](http://sourceforge.net/projects/win32diskimager/) ，解压后可以直接运行。

- 解压后，右键点击`Win32DiskImager.exe`，选择“**以管理员身份启动**”。

- 选择刚才解压好的树莓派系统镜像。

- 在磁盘列表中选择SD卡的盘符。请确保选择正确的盘符，否则硬盘上的数据可以丢失！如果Win32DiskImager无法找到你的SD卡插槽的SD卡，请尝试使用USB的SD卡读卡器。

- 点击`Write`按键，然后等待烧写完成。

- 烧写完成后退出Win32DiskImager，再弹出SD卡。

**注意：**系统镜像烧写好后（以Raspbian为例），Windows系统中看到的SD卡将变成一个只有55M左右大小的fat分区，这是正常的。因为系统镜像有两个分区，另一个分区是Linux专用的ext4，所以在Windows系统中无法直接查看该分区的文件系统。

---

*注：本文参考了eLinux的文章[RPi_Easy_SD_Card_Setup](http://elinux.org/RPi_Easy_SD_Card_Setup)，其许可证为： [Creative Commons Attribution-ShareAlike 3.0 Unported license](http://creativecommons.org/licenses/by-sa/3.0/)*
