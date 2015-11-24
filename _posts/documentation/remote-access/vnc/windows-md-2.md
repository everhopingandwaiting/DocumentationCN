---
ID: 491
post_title: 在Windows系统中通过VNC连接树莓派
author: 有聰哥冇甩拖
post_date: 2015-11-06 23:59:27
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/vnc/windows-md-2/
published: true
---
# 在Windows系统中通过VNC连接树莓派 

Windows系统用户需要下载并安装VNC客户端程序方可通过VNC连接树莓派。推荐使用TightVNC，请前往<a href="//www.tightvnc.com/download.php" target="_blank">tightvnc.com</a>下载。 

请按系统的架构选择32位或64位的版本，如果不确定，可以右键点击”这台电脑“，”属性“，再查看。下载完成后运行安装程序。 

安装过程中，程序会提示询问安装的类型，”典型“、”自定义“、抑或”完整“。这个情况下，只需要选择VNC客户端而无需选择VNC服务器，所以选择”自定义“。点击`TightVNC`后在弹出的菜单中选择`Entire Feature will be unavailable`，再点击`Next`。取消勾选防火墙选项再点击`Next`，然后点击`Install`。

 ![TightVNC Windows installation][1]

安装完成后，可以在“开始菜单”中的“应用程序”中找到`TightVNC Viewer`。运行时会看到下图所示的对话框。只需输入树莓派的IP地址，再加上端口号（`:0` or `:1`），例如：`192.168.0.6:1`。

![TightVNC connection dialog][2]

点击`Connect`按钮，程序将提示输入密码，将VNC服务启动时设定的密码输入，就可看见树莓派的桌面了。

![Raspberry Pi desktop][3]

如果想关闭连接，请勿在树莓派的桌面环境中点击退出，只要关闭当前TightVNC窗口即可，随后再用`kill`命令来关闭树莓派上运行的VNC服务器。

如需参考TightVNC Viewer 的使用说明文档，请前往<a href="//www.tightvnc.com/docs.php" target="_blank">tightvnc.com</a>。

 [1]: https://raw.githubusercontent.com/rpicn/documentation/master/remote-access/vnc/images/win/vnc-win-install.png
 [2]: https://raw.githubusercontent.com/rpicn/documentation/master/remote-access/vnc/images/win/vnc-win-connect.png
 [3]: https://raw.githubusercontent.com/rpicn/documentation/master/remote-access/vnc/images/win/vnc-win-connected.png
