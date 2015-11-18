---
ID: 554
post_title: SFTP
author: 有聰哥冇甩拖
post_date: 2015-11-17 16:26:08
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/ssh/sftp-md/
published: true
---
# SFTP

SFTP是通过SSH进行文件读取、传输、管理的网络协议。用户可以使用SFTP对树莓派上的文件进行更改、浏览、编辑等操作。与[FTP](../../ftp.md)不同，SFTP更容易设置，因为树莓派默认已开启SSH。

## FileZilla

先下载最新版本的<a href="https://filezilla-project.org/" target="_blank">filezilla-project.org</a>。

启动FileZilla然后前往`File`，`Site Manager`。

在弹出的对话框中输入IP地址，端口选择22，协议选择`SFTP`，再输入用户名和密码（树莓派默认的用户和密码分别是`pi`和`rasberry`）。

点击`Connect`就能登入树莓派，看到主目录了。

## 在Ubuntu系统中使用Nautilus

首先在本地打开Nautilus，然后选择`File`，`Connect to Server`，输入以下信息：

```
Type: SSH
Server: <The Pi's IP address>
Port: 22 (default)
User name: pi (default)
Password: raspberry (default)
```

其他参考：[IP地址](../../../troubleshooting/hardware/networking/ip-address.md)。

