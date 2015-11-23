---
ID: 580
post_title: 在Windows系统通过SSH连接树莓派
author: 有聰哥冇甩拖
post_date: 2015-11-19 15:45:01
post_excerpt: ""
layout: post
permalink: >
  https://www.rpicn.org/documentation/remote-access/ssh/windows-md-3/
published: true
---
# 在Windows系统通过SSH连接树莓派

在Windows系统上通过SSH连接树莓派需要下载SSH客户端。最常用的一款SSH客户端名称为PuTTY，可前往<a href="http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html" target="_blank">greenend.org.uk</a>下载。

在`For Windows on Itel x86`栏目下找到`putty.exe`，再点击下载。

下载到的文件不是一个安装包，只是一个单独的`.exe`文件。第一次运行的时候，将会看到下面的画面：

![PuTTY configuration](https://raw.githubusercontent.com/raspberrypi/documentation/master/remote-access/ssh/images/ssh-win-config.png)

在`Host Name`一栏中输入树莓派的IP，然后点击`Open`，如果点击了之后没有任何反应而且最后显示一句错误信息`Network error: Connection timed out`则可能输入的IP有误。

如果不知道树莓派的IP地址，可以在树莓派本机上输入命令`hostname -I`来查询。如需更多关于树莓派IP地址的信息，请浏览[IP地址](../../../troubleshooting/hardware/networking/ip-address.md)。

如果连接成功，程序会弹出下图所示的安全警告，在内网中通常可以信任，点击`Yes`按钮。每当连接一个以前没连接过的主机，PuTTY都会有这样的安全提示。

![PuTTY warning](https://raw.githubusercontent.com/raspberrypi/documentation/master/remote-access/ssh/images/ssh-win-warning.png)

连接成功后就会见到平时的命令行提示，先输入用户名和密码，跟在树莓派上登入的信息一样。树莓派默认的用户名是`pi`，密码是`raspberry`，出于安全原因，密码输入时不会看到“*”号提示密码位数，用户需要盲输密码。

这时应该可以看到树莓派的命令行提示符，这个提示符和在树莓派本机上登入时看到的一样。

```
pi@raspberrypi ~ $
```

![PuTTY window](https://raw.githubusercontent.com/raspberrypi/documentation/master/remote-access/ssh/images/ssh-win-window.png)

只要输入`exit`命令，就可以关闭PuTTY窗口。

下次使用PuTTY通过SSH登入树莓派时，可以在设置窗口的下方找到`Saved Sessions`一栏填入会话名称，再点击`Save`保存。但是，建议在窗口左边一栏找到`Connection`页面，再在`Seconds between keepalives`的时间选择`30`，然后再次回到`Sessions`页面中，再点击一次`Save`保存以上的设置。使用这个设置，即使长时间没指令的情况下，PuTTY的与树莓派的连接也不会很快断开。

如需参考PuTTY更详细的说明文档，请参考<a href="http://www.chiark.greenend.org.uk/~sgtatham/putty/docs.html" target="_blank">PuTTY Docs</a>。
