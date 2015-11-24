---
ID: 504
post_title: 在Linux或Mac OS系统通过SSH连接树莓派
author: 有聰哥冇甩拖
post_date: 2015-11-09 23:16:13
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/ssh/unix-md/
published: true
---
# 在Linux或Mac OS系统通过SSH连接树莓派

用户可以在一台运行Linux或Mac OS系统的电脑（或者另一个树莓派）上使用终端通过SSH连接树莓派，而无需另外安装其他软件。

连接前，用户需要知道树莓派的IP地址，可以在树莓派上的终端输入`hostname -I`。

另外，对于树莓派没连接显示器的用户，可以通过路由器的Web管理页面上查看，或者使用其他工具例如`nmap`，详细信息请参考[IP地址](../../../troubleshooting/hardware/networking/ip-address.md)文档。

要从另一台电脑连接到树莓派，输入下面的命令，请将`<IP>`替换成树莓派的IP地址：

    ssh pi@<IP>

如果提示错误信息`connection timed out`，很可能是因为输入的树莓派IP地址有误。

如果成功建立了连接，终端会显示一个提示，需要用户检验数字证书的指纹，如果在局域网内连接一般不会有问题，输入`yes`然后按`Enter`继续。这个检验只会在第一次连接时出现。

如果树莓派获得的IP地址是以往其他设备（甚至是其他局域网的）使用过，而且用户也曾经通过SSH连接该设备的话，可能会显示安全警告，提示数字证书已更改，这时可以先按提示输入命令清除已知设备的数字证书。命令应该是类似`ssh-keygen -R <IP>`的，同样地，请将`<IP>`替换成树莓派的IP地址。最后再用`ssh`命令应该可能成功连接了。

然后需要输入`pi`的密码，Raspbian系统预设`pi`用户的密码为`raspberry`，出于安全原因，密码需要盲输。成功登入系统后将可看到与树莓派的命令行提示符。

如果需要使用其他用户名登入，只要在`ssh`命令中作相应的改动便可，例如：`ssh eben@192.168.1.5`。

    eben@raspberrypi ~ $

这时说明已成功通过SSH远程连接树莓派，也可以执行命令了。

如需参考`ssh`命令的说明文档，只需在终端输入`man ssh`。

如需使用公钥私钥配对来设置免密码SSH连接，请参考[免密码SSH连接](../passwordless.md) 指引。
