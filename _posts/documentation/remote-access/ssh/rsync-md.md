---
ID: 322
post_title: rsync自动同步
author: 有聰哥冇甩拖
post_date: 2015-10-26 14:34:17
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/ssh/rsync-md/
published: true
---
# rsync

用户可以使用`rsync`在不同的电脑之间互相同步。比如在台式电脑或者手提电脑和树莓派之间同步文件，又或者树莓派拍好的照片自动同步到电脑上。通过SSH协议使用`rsync`就可以自动与其他电脑同步了。

本文所举的例子，可以设置树莓派与一台Linux电脑同步一个照片文件夹：

首先在电脑上新建一个名为`camera`的文件夹：

```
mkdir camera
```

再登入树莓派，执行`hostname -I`命令来查询IP地址。本文的例子中，假设树莓派已设置好，会定时摄影然后加时间戳再保存在SD卡的`camera`文件夹中。

现在在电脑执行下面的命令（先按实际情况将树莓派的IP地址替换好）：

```
rsync -avz -e ssh pi@192.168.1.10:camera/ camera/
```

这个命令会从将树莓派上`camera`文件夹中的所有文件复制到电脑上的`camera`文件夹中去。

如果需要定时执行这个命令，可以在[cron](../../linux/usage/cron.md)中执行。