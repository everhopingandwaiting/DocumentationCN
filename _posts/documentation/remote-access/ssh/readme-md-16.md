---
ID: 313
post_title: SSH
author: 有聰哥冇甩拖
post_date: 2015-10-26 11:55:19
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/ssh/readme-md-16/
published: true
---
# SSH (Secure Shell)

用户可以使用`ssh`命令在网络上的另一台电脑远程连接树莓派，进入命令行界面。

请注意：通过`ssh`只可进入命令行界面，而不是图形化的桌面环境。如果需要进入桌面，请参考[VNC](../../vnc/README.md)或在Windows上使用<a href="http://mobaxterm.mobatek.net/" target="_blank">MobaXterm</a>。

同时，用户亦可以更改SSH服务器的设定选择启用或禁用SSH服务（默认是已启用的），只要使用[raspi-config](../../../configuration/raspi-config.md)便可轻松切换：

在终端中输入：

`sudo raspi-config`

找到`ssh`，按下`Enter`，然后就可选择启用或禁用SSH服务器了。

Linux的各个发行版和Mac OS操作系统都预装SSH客户端，Windows系统可以安装第三方的SSH客户端，请按不同的操作系统选择下列的文档：


- [Linux & Mac OS](../unix.md)
- [Windows](../windows.md)
