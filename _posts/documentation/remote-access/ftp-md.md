---
ID: 459
post_title: FTP服务器
author: 有聰哥冇甩拖
post_date: 2015-10-30 23:28:41
post_excerpt: ""
layout: post
permalink: >
  https://www.rpicn.org/documentation/remote-access/ftp-md/
published: true
---
# FTP服务器

用户可以使用FTP（文件传输协议）让树莓派和其他电脑互相传输文件。虽然Raspbian自带的程序`sftp-server`可以让有着特定权限的用户传输文件和目录，但是很多时候还是需要限制他们的文件读取权限的。本文将介绍如何使用Pure-FTP搭建一个FTP服务器：

## 安装Pure-FTPd

首先安装`Pure-FTPd`，在终端输入下面的命令：


    sudo apt-get install pure-ftpd


## 基本设置

先新建一个名为`ftpgroup`的用户组，再新建一个名为`ftpuser`的用户，但是这个“用户”不可以登入系统，也不可以有自己的主目录。在终端输入以下命令：

    groupadd ftpgroup;
	useradd ftpuser -g ftpgroup -s /sbin/nologin –d /dev/null


### FTP目录，虚拟用户及虚拟用户组

假设需要新建一个名为`FTP`的目录。

    sudo mkdir /home/pi/FTP

然后将所有者改为`ftpuser`，再改权限为755：

    sudo chown -R ftpuser:ftpgroup /home/pi/FTP；
	sudo chmod -R 755 /home/pi/FTP;

再新建一个名为`upload`的虚拟用户，映射到`ftpuser`和`ftpgroup`去，将其主目录设定为`/home/pi/FTP`，再把密码存在Pure-FTPd的数据库中：

    sudo pure-pw useradd upload -u ftpuser -g ftpgroup -d /home/pi/FTP -m

输入了这个命令之后，程序会提示设定该用户的密码，需要盲输。其后建立虚拟用户数据库，在终端输入：

    sudo pure-pw mkdb

最后，也是最重要的，是指定校验密码方法的优先值，只需要为`/etc/pure-ftpd/conf/PureDB`在`/etc/pure-ftpd/auth`目录中建立一个软链，在软链的文件名前加一个足够小的数字就可以了，例如`60`。在终端输入：

    ln -s /etc/pure-ftpd/conf/PureDB /etc/pure-ftpd/auth/60puredb

重新启动Pure-FTPd：

    sudo service pure-ftpd restart

这时可以使用FTP客户端，例如FileZilla，来测试服务器了。

## 更多的设置

The configuration of Pure-FTPd is simple and intuitive. The administrator only needs to define the necessary settings by making files with option names, like `ChrootEveryone`, and typing `yes`, then storing in the directory `/etc/pure-ftpd/conf`, if all FTP users are to be locked in their FTP home directory (`/home/pi/FTP`). Here are some recommended settings:

```bash
sudo nano /etc/pure-ftpd/conf/ChrootEveryone
```

Type `yes`, and press ``Ctrl+X``, ``Y``, and ``Enter``.

Likewise,

make a file named `NoAnonymous` and type `yes`;

make a file named `AnonymousCantUpload` and type `yes`;

make a file named `AnonymousCanCreateDirs` and type `no`;

make a file named `DisplayDotFiles` and type`no`;

make a file named `DontResolve` and type `yes`;

make a file named `ProhibitDotFilesRead` and type `yes`;

make a file named `ProhibitDotFilesWrite` and type `yes`;

make a file named `FSCharset` and type`UTF-8`;

...

Restart `pure-ftpd` again and apply the above settings.


    sudo service pure-ftpd restart


想查询Pure-FTPd的其他信息和官方文档，请浏览<a href="http://www.pureftpd.org/project/pure-ftpd" target="_blank">Pure-FTPd的官方网站</a>。
