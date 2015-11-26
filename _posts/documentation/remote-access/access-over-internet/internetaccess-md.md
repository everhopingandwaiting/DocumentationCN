---
ID: 306
post_title: 通过互联网连接树莓派
author: 有聰哥冇甩拖
post_date: 2015-10-26 11:12:57
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/access-over-internet/internetaccess-md/
published: true
---
# 通过互联网连接树莓派

用户可以通过互联网，在另一台电脑或移动设备上连接到树莓派。

其中一个方法是在路由设置端口映射，需要在路由设置，将外部端口映射到局域网内树莓派的端口。现在市面上的路由一般都提供这个功能，但是可能不同型号的路由器设置称谓有所不同，请在路由器说明书中查阅“虚拟服务器”或“端口映射”又或者“端口转发”。防火墙内或者多层局域网内的树莓派可能需要更复杂的设置。端口映射的弊端是将局域网内的端口向广域网暴露了，已知一个安全漏洞可能因此带来危险，需要引起注意。

## Weaved

更安全的方法可以考虑使用Weaved，Weaved与端口映射有不同。Weaved是安装在树莓派上的软件，让用户可以通过互联网远程连接树莓派。SSH，VNC，HTTP，SFTP等使用TCP连接的服务都可以无需设置端口映射就可以实现远程连接了。

先在树莓派上更新Raspbian的安装包列表（在树莓派本机或SSH连接后在终端操作均可）：
  
    sudo apt-get update

安装`weavedconnectd`:

    sudo apt-get install weavedconnectd

然后运行`weavedinstaller`。

Next run the weavedinstaller.  The weavedinstaller will ask you to input your Weaved account user name (email) and password.  You can create a Weaved user account here: https://developer.weaved.com/portal/index.php.   After you have created an account, go back to the Pi command line window.  Enter the command below to run the weavedinstaller on your Pi.  Follow the on-screen instructions in the Pi terminal window.

    sudo weavedinstaller

Your Weaved account is now a private Internet VPN connection service to your Pi without port forwarding.  Access your Pi by logging in to your account at www.weaved.com.

如需更多帮助，请致电邮至<a href="mailto:support@weaved.com">support@weaved.com</a>。

## 花生壳