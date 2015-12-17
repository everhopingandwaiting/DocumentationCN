---
ID: 471
post_title: 在Linux系统中通过VNC连接树莓派
author: 有聰哥冇甩拖
post_date: 2015-11-01 23:09:51
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/vnc/linux-md-2/
published: true
_theme_show_post_title: 0
---
# 在Linux系统中通过VNC连接树莓派

Linux发行版一般会附带一个名为`Remote Desktop Viewer`的应用程序，用户可以使用该程序连接树莓派。该程序通常可以在`Applications / Internet`菜单中找到（以下为Ubuntu的示例）。

![VNC in Ubuntu Applications menu](https://github.com/rpicn/documentation/raw/master/remote-access/vnc/images/linux/vnc-ubuntu-menu.png)

打开了`Remote Desktop Viewer`后，将会看到下面的对话框。选择`VNC`协议，然后输入树莓派的IP地址，接着加上端口号（`:0`或`:1`）。例如：`192.168.0.6:1`

![Connection dialog](https://github.com/rpicn/documentation/raw/master/remote-access/vnc/images/linux/vnc-ubuntu-connect.png)

点击`Connect`按钮，程序会提示询问密码，将VNC服务启动时设定的密码输入，就可看见树莓派的桌面了。

![Raspberry Pi desktop](https://github.com/rpicn/documentation/raw/master/remote-access/vnc/images/linux/vnc-ubuntu-connected.png)

如果想关闭连接，请勿在树莓派的桌面环境中点击退出，只要关闭当前Remote Desktop Viewer窗口即可，随后再用`kill`命令来关闭VNC服务器。

远程桌面客户端非常多，例如也可以使用一款名为`Remmina Remote Desktop Client`的程序，前往<a href="http://remmina.sourceforge.net" target="_blank">remmina.sourceforge.net</a>下载。
