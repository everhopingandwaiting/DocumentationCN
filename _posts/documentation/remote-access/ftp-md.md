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
_theme_show_post_title: 0
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

Pure-FTPd的设置简单直观。管理员只需要在`/etc/pure-ftpd/conf`目录中建立一个文件，以选项名为文件名，再将设定内容写入文件中即可。例如，如果需要将用户锁定在其各自的根目录，只要在这个目录中新建一个名为`ChrootEveryone`的文件，再写入`yes`，就可以了。下面是一些基本的设置建议：

先在终端输入：

    sudo nano /etc/pure-ftpd/conf/ChrootEveryone

再写入`yes`，按下`Ctrl`和`X`后，按`Y`，再按`Enter`，保存修改后退出。

同样地，继续：

新建一个名为`NoAnonymous`的文件，写入`yes`；

新建一个名为`AnonymousCantUpload`的文件，写入`yes`；

新建一个名为`AnonymousCanCreateDirs`的文件，写入`no`；

新建一个名为`DisplayDotFiles`的文件，写入`no`；

新建一个名为`DontResolve`的文件，写入`yes`；

新建一个名为`ProhibitDotFilesRead`的文件，写入`yes`；

新建一个名为`ProhibitDotFilesWrite` 的文件，写入`yes`；

新建一个名为`FSCharset`的文件，写入`UTF-8`；

……

再次重启`pure-ftpd`，使上面的设置生效。


    sudo service pure-ftpd restart


想查询Pure-FTPd的其他信息和官方文档，请浏览<a href="http://www.pureftpd.org/project/pure-ftpd" target="_blank">Pure-FTPd的官方网站</a>。
