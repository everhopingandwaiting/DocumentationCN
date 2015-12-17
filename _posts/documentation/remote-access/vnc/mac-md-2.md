---
ID: 483
post_title: 在Mac系统中通过VNC连接树莓派
author: 有聰哥冇甩拖
post_date: 2015-11-05 23:58:25
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/vnc/mac-md-2/
published: true
_theme_show_post_title: 0
---
# 在Mac系统中通过VNC连接树莓派

Mac用户需要安装VNC客户端程序。当然也可以使用“共享屏幕”（系统自带），但这样需要复杂的设置。RealVNC可以与树莓派的VNC服务器对接，请前往<a href=”http://www.realvnc.com/download/vnc/latest” target=”_blank”>realvnc.com</a>下载。

压缩包下载完成后解压安装。在选择安装类型时只需选择“VNC客户端”，如下图所示：

![VNC OSX installation](https://raw.githubusercontent.com/rpicn/documentation/master/remote-access/vnc/images/osx/vnc-osx-install.png)

点击`Continue`继续进行其余的步骤。完成安装后，打开Finder，在窗口的左边点击“程序”，然后在搜索栏中输入“vnc”进行搜索，如有必要，可以在Dock中添加VNC客户端的快捷方式。

![VNC connection dialog](https://raw.githubusercontent.com/rpicn/documentation/master/remote-access/vnc/images/osx/vnc-osx-connect.png)

进行时会出现一个这样的对话框，请输入树莓派的IP地址，再指定端口号（`:0`或`:1`），例如：`192.168.0.165:1`。

点击`Connect`按钮，程序会出现下图所示的未加密连接警告：

![Unencrypted connection warning](https://raw.githubusercontent.com/rpicn/documentation/master/remote-access/vnc/images/osx/vnc-osx-warning.png)

通常如果用户需要通过互联网连接树莓派，必须作斟酌。但如果用户通过局域网或者学校内部网络连接树莓派的话，则毋须担心。点击*Continue*后再输入较早前在树莓派上架设VNC服务器时所设定的密码，验证成功后就能查看树莓派的桌面。

![Raspberry Pi desktop](https://raw.githubusercontent.com/rpicn/documentation/master/remote-access/vnc/images/osx/vnc-osx-connected.png)

如果想关闭连接，请勿在树莓派的桌面环境中点击退出，只要关闭当前RealVNC的窗口即可，随后再用`kill`命令来关闭树莓派上运行的VNC服务器。

如需参考RealVNC的使用说明文档，请前往<a href=”http://www.realvnc.com/products/vnc/documentation/latest/” target=”_blank”>这个页面</a>。
