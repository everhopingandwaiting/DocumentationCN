---
ID: 70
post_title: VNC (虚拟网络计算机)
author: 有聰哥冇甩拖
post_date: 2015-10-17 01:26:29
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/vnc/readme-md-3/
published: true
_theme_show_post_title: 0
---
# VNC (虚拟网络计算) 

当无法直接在树莓派上操作时，用户可能需要在另一台电脑上远程控制树莓派。 VNC是一个图形化桌面共享系统，可以让用户在一台电脑上远程另一台。用户在主控端的输入指令会被传输到被控端，被控端的返回信息和屏幕更新也会被传输到主控端。 在主控端电脑的显示窗口可以显示树莓派的桌面，用户可以通过该窗口远控树莓派。 

- 在树莓派上安装TightVNC（在树莓派本机的终端安装或通过[SSH][1]客户端用命令行安装）:

```
sudo apt-get install tightvncserver 
```

- 然后启动TightVNC服务，服务器将会提示，请管理员设定一个仅供查看的密码：

```
tightvncserver
```

- 在终端启动一个VNC服务。下面的例子在`:0`端口启动了一个全高清的会话：

```
vncserver :0 -geometry 1920x1080 -depth 24
```

- 接下来在主控端安装并运行VNC客户端： 
    - 在Linux系统中，安装`xtightvncviewer`：
    `sudo apt-get install xtightvncviewer` 
    - 在其他系统中，请浏览[TightVNC.com][2]下载相应平台的客户端。

### 开机自动运行

#### 如果嫌每次敲一条长长的命令太麻烦，可以创建一个启动VNC服务器的脚本文件：

- 创建一个名为`vnc.sh`（供参考）的脚本：

`cd`
`sudo nano vnc.sh` 

- 然后输入以下内容：

`#!/bin/sh`
`vncserver :0 -geometry 1920x1080 -depth 24 -dpi 96`

- 然后按`Ctrl`和`X`（意思为退出），此时`nano`会提示询问是否保存，再按`Y`（即：确认保存），最后按下`Enter`，完成脚本的保存。

- 添加执行权限：

```
chmod +x vnc.sh
```

- 这样之后，如果想启动VNC服务，只需要在终端输入：

```
./vnc.sh
```

#### 如果希望VNC服务器在开机后自动运行，只需要在树莓派上创建一个脚本文件便可实现：

- 在终端以root登入树莓派：

```
sudo su
```

- 切换到`/etc/init.d/`目录：

```
cd /etc/init.d/
```

- 在该目录下创建一个名为`vncboot`（供参考）的脚本：
```
nano vncboot
```

- 输入以下内容：

`###BEGIN INIT INFO`
`#Provides: vncboot`
`#Required-Start: $remote_fs $syslog`
`#Required-Stop: $remote_fs $syslog#`
`#Default-Start: 2 3 4 5#`
`#Default-Stop: 0 1 6#`
`#Short-Description: Start VNC Server at boot time#`
`#Description: Start VNC Server at boot time.#`
`###END INIT INFO`
`#! /bin/sh`
`#/etc/init.d/vncboot`

`USER=root`
`HOME=/root` 

`export USER HOME`

`case "$1" in`
` start)`
`  echo "Starting VNC Server"`
`  #Insert your favoured settings for a VNC session`
`  /usr/bin/vncserver :0 -geometry 1280x800 -depth 16 -pixelformat rgb565`
`  ;;`

`stop)`
`  echo "Stopping VNC Server"`
`  /usr/bin/vncserver -kill :0`
`  ;;`

`*)`
`  echo "Usage: /etc/init.d/vncboot {start|stop}"`
`  exit 1`
`  ;;`
`esac`

`exit 0`

- 然后按`Ctrl`和`X`（意思为退出），此时`nano`会提示询问是否保存，再按`Y`（即：确认保存），最后按下`Enter`，完成脚本的保存。

- 添加执行权限：

```
chmod 755 vncboot
```

- 添加到启动运行队列：
```
update-rc.d /etc/init.d/vncboot defaults
```

- 如果添加成功，系统会返回：
```
update-rc.d: using dependency based boot sequencing
```

- 但如果系统返回的是：
```
update-rc.d: error: unable to read /etc/init.d//etc/init.d/vncboot
```

- 则再尝试如下命令：
```
update-rc.d vncboot defaults
```

- 重启树莓派，VNC服务便将自动启动。

（译者注：为照顾新玩家，本段文字作了一点小改动。）

现在就可以在电脑或手提电脑甚至手机中使用**VNC客户端**远程连接树莓派了。不同系统上的VNC客户端使用说明如下： 
- [Linux][3]
- [Mac OS][4]
- [Windows][5]

---
*注：本文参考了eLinux的文章[RPi VNC server][6], 其许可证为：[Creative Commons Attribution-ShareAlike 3.0 Unported license][7]。*

 [1]: ../ssh/README.md
 [2]: http://www.tightvnc.com/download.php
 [3]: ../linux.md.2
 [4]: ../mac.md.2
 [5]: ../windows.md.2
 [6]: http://elinux.org/RPi_VNC_Server
 [7]: http://creativecommons.org/licenses/by-sa/3.0/
