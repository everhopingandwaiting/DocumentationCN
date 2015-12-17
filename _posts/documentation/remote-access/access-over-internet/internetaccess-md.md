---
ID: 306
post_title: 通过互联网连接树莓派
author: 有聰哥冇甩拖
post_date: 2015-10-26 11:12:57
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/access-over-internet/internetaccess-md/
published: true
_theme_show_post_title: 0
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

然后运行`weavedinstaller`。`weavedinstaller`会询问用户在Weaved网站上的账号（邮箱地址）和密码。用户可以移步到<a href="https://developer.weaved.com/portal/index.php" target="_blank">这个网页</a>注册。注册好后可以在树莓派的命令行中输入Weaved的账号和密码后继续按屏幕的指引安装。

    sudo weavedinstaller

安装完成后，树莓派就已经接入一个虚拟私有网络（VPN）中了，而且无需设置端口映射。需要登入到树莓派的话，只要登入<a href="http://www.weaved.com" target="_blank">www.weaved.com</a>，再按网站上的指引继续。

如需更多帮助，请致电邮至<a href="mailto:support@weaved.com">support@weaved.com</a>。

## <a href="http://www.oray.com">Oray.com</a>的花生壳、向日葵及蒲公英等服务或产品

<a href="http://www.oray.com">Oray.com</a>是国内知名互联网服务商，旗下产品众多，而且适合用于远程连接树莓派这个场景的话，软件服务方面有<a href="http://hsk.oray.com/download/#type=http|shumeipai" target="_blank">花生壳</a>、<a href="http://sunlogin.oray.com/zh_CN/" target="_blank">向日葵</a>，硬件产品有<a href="http://pgy.oray.com/" target="_blank">蒲公英</a>。

- <a href="http://hsk.oray.com/download/#type=http|shumeipai" target="_blank">花生壳（动态域名）</a>：有公网IP或网络运营商允许端口转发的用户适用，旧版源码有公开，但新版源码并没公开；
- <a href="http://sunlogin.oray.com/zh_CN/" target="_blank">向日葵（远程监控）</a>：可以在浏览器中SSH远程连接，没公网IP或支营商不允许端口转发的用户适用；遗憾的是厂商没有公开源码，也没适合树莓派安装的版本；
- <a href="http://pgy.oray.com/" target="_blank">蒲公英（智能路由）</a>：内嵌了<a href="http://hsk.oray.com/download/#type=http|shumeipai" target="_blank">花生壳内网版</a>和<a href="http://sunlogin.oray.com/zh_CN/hardware/" target="_blank">向日葵远程开机模块</a>的智能无线路由器，仅售¥198！

现在一般市面上的国产路由，也集成了花生壳的网页版，如果运营商不允许常用端口的转发，通常是无法直接远程连接的，建议考虑购买功能超多的智能路由<a href="http://pgy.oray.com/" target="_blank">蒲公英</a>。

