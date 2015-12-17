---
ID: 577
post_title: 用Apache在树莓派上搭建网页服务器
author: 有聰哥冇甩拖
post_date: 2015-11-19 17:09:16
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/web-server/apache-md/
published: true
_theme_show_post_title: 0
---
# 用Apache在树莓派上搭建网页服务器

Apache是一个受欢迎的网站服务器程序，还可以安装在树莓派上搭建服务器。

除了可满足静态页面服务之外，加载其他模块后，Apache还可以作为动态网页服务器，例如PHP。

## 安装Apache

首先，在终端输入以下命令，安装`apache2`：

    sudo apt-get install apache2 -y

## 测试网页服务器

安装完成后，Apache会自动在默认的网页存放目录中保存一个示例网页（一个HTML文件）。当本地用户浏览`http://localhost/`或其他用户通过内网中的电脑浏览`http://192.168.1.10`（具体按树莓派的内网IP地址为准），就会显示这个网页。如果不知道树莓派的IP地址，可以在终端中输入命令`hostname -I`查询（如需更多帮助，请浏览[IP address](../../../troubleshooting/hardware-troubleshooting/networking/ip-address.md)）。

无论是本机查看抑或是局域网内查看，如果看到下面的画面，说明Apache工作正常！

![Apache success message](https://github.com/rpicn/documentation/raw/master/remote-access/web-server/images/apache-it-works.png )

### 更改默认网页目录

默认的示例网页的路径为`/var/www/html/index.html`。

**注意：Raspbian Wheezy版本，默认的网页存放路径为`/var/www`，但Raspbian Jessie版本是`/var/www/html/`。**

可先前往这个目录查看一下里面的文件：

    cd /var/www/html
    ls -al

系统会显示：

    total 12
    drwxr-xr-x  2 root root 4096 Jan  8 01:29 .
    drwxr-xr-x 12 root root 4096 Jan  8 01:28 ..
    -rw-r--r--  1 root root  177 Jan  8 01:29 index.html

这说明`/var/www/html/`目录下有一个名为`index.html`的文件。`.`指的是`/var/www/html/`目录自己本身，而`..`指的是父级目录，即`/var/www/`。

### 这些信息的详细含义

1. 第一栏是文件或目录的权限；
2. 第二栏是指该目录下的文件（或目录）数量；
3. 第三栏是指该文件或目录的所有者；
4. 第四栏是指该文件或目录的所属用户组；
5. 第五栏是文件大小；
6. 第六栏是最后一次修改的日期和时间；

可以看到默认的`html`目录和`index.html`文件的所有者均为`root`用户。如果需要编辑，则需要获得`root`的权限。修改之前，可以用这条命令更改所有权：`sudo chown pi: index.html`。（译者注：网页目录及网页文件的所有者和所属用户组应该为`www-data`？）

如果改动了这个网页，可以尝试刷新一下浏览器查看一下变化。

### 搭建专属网站

如果用户通晓HTML，可以在网页目录存放HTML文件以有其他资源，在树莓派上搭建成一个可供局域网浏览的网站。

## 进阶 - 安装PHP

如果需要让Apache处理PHP网页，需要先安装PHP5以及Apache需要用到的模块，在终端输入以下命令：

    sudo apt-get install php5 libapache2-mod-php5 -y

现在先将`index.html`删除：

    sudo rm index.html

再新建一个名为`index.php`的文件。

    sudo nano index.php

然后在这个文件中写入一些PHP语句，比如，先输入`sudo nano index.php`，然后复制下列语句：

    <?php echo "hello world"; ?>

按下`Ctrl`加`X`，再按下`Y`，再按下`Enter`，这样就保存了刚才的更改。这时刷新浏览器，应该可以看到“hello world”。这个网页还是静态但能说明PHP已正常工作，下面这句是动态的：

    <?php echo date('Y-m-d H:i:s'); ?>

又或者用这句查看PHP的信息：

    <?php phpinfo(); ?>

### 再进一步 - WordPress

现在Apache和PHP已安装并正常运行，用户还可以更进一步，在树莓派上架设一个WordPress站点，请参考[WordPress安装说明](../../../usage/wordpress/README.md)
