---
ID: 419
post_title: Linux
author: 有聰哥冇甩拖
post_date: 2015-10-26 22:25:04
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/installation/installing-images/linux-md/
published: true
---
# 在Linux系统中使用镜像安装系统

**注意：**本文所用的工具`dd`可以擦写硬盘上的所有扇区。如果按本文指引输入的命令中，使用的盘符万一出错，将可能导致无法挽回的数据损失。请谨慎使用！（译者曾作s……）

首先检查一下当前有哪些储存设备已加载，输入命令：

`sudo df -h`

- 如果电脑有SD卡插槽，就使用SD卡插槽；如果没有，就使用USB的SD卡读卡器。

- 再次输入`sudo df -h`，自动挂载新的储存设备应该会显示出来，就是刚才插入的SD卡。左边一栏是SD卡的设备名称，可能显示成`/dev/mmcblk0p1`或者是`/dev/sdd1`。设备名称最后的部分，`/dev/mmcblk0p1`中的`p1`或`/dev/sdd1`中的`1`，意思就是这个储存设备的第几个分区。但烧写SD卡需要对整个储存设备进行操作，而不仅对一个分区，所以稍后将会使用的设备名称应该是`/dev/mmcblk0`或`/dev/sdd`。需要注意的是，如果成功烧写SD卡后，会出现两次，因为Raspbian的SD卡镜像中有两个分区。

- 获得储存设备名称后，SD卡需要先取消挂载方可进行烧写。

- 输入命令：
    `sudo umount /dev/sdd1`
    如果设备名称不是`sdd1`，只需替换为实际的设备名称即可。

- 如果刚才的`df`命令得到系统的返回显示SD卡不只一个分区，则需要取消所有分区的挂载后方可进行下一步。

- 在终端使用命令将镜像烧写到SD卡中。下面的命令中，`if=`（“input file”的缩写）后面要确保镜像的路径名没写错，`of=`（“output file”的缩写）后面同样要确保储存设备的名称没写错。**注意：**万一写错了储存设备的名称将可能导致无法挽回的数据损失。另外，设备名称应该是整个储存设备而不只是某个分区，例如，应该是`sdd`，而不是`sdds1`，`sddp1`；或者应该是`mmcblk0`而不是`mmcblk0p1`。烧写命令为：

`sudo dd bs=4M if=2015-09-24-raspbian-jessie.img of=/dev/sdd`

- 需要指出的是，`bs`（“block size”，即分块大小）如果指定为`4M`，通常不会有什么问题。万一不成功，建议尝试更为`1M`，但是烧写SD卡的时间可能会更长。

- 如果用户不是以`root`身份登入系统的话，命令的开关需要加上`sudo`。（译者注：`sudo`就好像一个令牌，临时告诉系统当前用户其实是超级用户大Boss！:D）

- `dd`命令在执行的过程中并不会显示执行进度，命令行的光标会眨眼，表示电脑在工作中，可能五分钟后才能完成烧写。另外，如果使用了带指示灯的读卡器，指示灯在烧写的过程中会快速闪烁。如果非要查看烧写的进度不可，可以在另一个终端中执行命令`sudo pkill -USR1 -n -x dd`，稍后，原来正在执行`dd`命令的终端会显示其进度。

- 除了`dd`之外，用户也可使用`dcfldd`程序来烧写SD卡，这个程序可以显示烧写进度。

- SD卡烧写完毕后，如果需要校验写入到SD卡的数据跟原来镜像文件的数据是否一致，可以将`dd`刚才烧写到SD卡的数据写回硬盘的一个新的.img文件中，再将文件尺寸改回原来镜像的大小，最后使用`diff`（或者`md5sum`）比较两个镜像文件的特征。

- SD卡的大小总会比原镜像文件的大小更大，而`dd`又会将整个SD卡（包括空的位置）一并复制出来，所以需要缩小新复制出来的镜像，目标的尺寸是原镜像的大小。请确保`if=`后面的储存设置名称没错误。`diff`可以非常容易地分辨出二者是否同样。以下为校验的方法：

`sudo dd bs=4M if=/dev/sdd of=from-sd-card.img`
`truncate --reference 2015-02-16-raspbian-wheezy.img from-sd-card.img`
`diff -s from-sd-card.img 2015-02-16-raspbian-wheezy.img`

- 运行`sync`，刷新缓存，SD卡的挂载就解除了。

- 拔出SD卡吧！

---

*注：本文参考了eLinux的文章[RPi_Easy_SD_Card_Setup](http://elinux.org/RPi_Easy_SD_Card_Setup)，其许可证为：[Creative Commons Attribution-ShareAlike 3.0 Unported license](http://creativecommons.org/licenses/by-sa/3.0/)*
