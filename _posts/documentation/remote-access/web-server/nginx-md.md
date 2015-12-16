---
ID: 701
post_title: 用nginx在树莓派上搭建网页服务器
author: admin
post_date: 2015-12-16 10:33:02
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/web-server/nginx-md/
published: true
---

# 用nginx在树莓派上搭建网页服务器

NGINX（读音为“engin-x”，前半部分与“发动机，引擎”发音一样）是一个受欢迎的轻量级网页服务器程序，在树莓派上亦可安装。

与Apache一样，NGINX可以做HTTP的服务器，提供静态或动态网页（如PHP）的浏览。

## 安装NGINX

首先在终端输入下列命令安装`nginx`：

    sudo apt-get install nginx

再启动服务器：

    sudo /etc/init.d/nginx start

## 测试NGINX

默认情况下，NGINX会在网页目录下放置一个测试用的HTML文件。如果在本机访问，可以前往`http://localhost/`浏览；如果在局域网内的其他电脑中访问，可以前往`http://192.168.1.10`（地址以树莓派的实际局域网IP为准）。如果不清楚树莓派的IP，可以在树莓派本机的终端输入`hostname -I`查询，如需更多信息，请参考[IP地址](../../../troubleshooting/hardware/networking/ip-address.md)。

无论在树莓派本机或在局域网内的电脑上浏览，都应该可以看到如下画面：

![NGINX welcome page](https://raw.githubusercontent.com/rpicn/documentation/master/remote-access/web-server/images/nginx-welcome.png)

### 更改默认页面

在Raspbian中，NGINX的默认网页目录设置为`/usr/share/nginx/www`，找到这个目录，替换或编辑该index.html即可。

## 进阶 – 安装PHP

    sudo apt-get install php5-fpm

### 在NGINX中启用PHP

在终端中输入如下命令，编辑`/etc/nginx/sites-enabled/default`：

    sudo nano /etc/nginx/sites-enabled/default

在文件大约第25行中（按下`Ctrl`不放，再按`C`，可显示行号），找到这句：

    index index.html index.htm;

在`index`后加入`index.php`，让该行变为：

    index index.php index.html index.htm;

然后再往下滚动，直至找到这几行：

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    # location ~ \.php$ {

从`location`出现那行起开始编辑，替换为下面几行：

    location ~ \.php$ {
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_pass unix:/var/run/php5-fpm.sock;
        fastcgi_index index.php;
        include fastcgi.conf;
    }

然后这几行应该改成这样：

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    location ~ \.php$ {
            fastcgi_split_path_info ^(.+\.php)(/.+)$;
    #       # NOTE: You should have "cgi.fix_pathinfo = 0;" in php.ini
    #
    #       # With php5-cgi alone:
    #       fastcgi_pass 127.0.0.1:9000;
            # With php5-fpm:
            fastcgi_pass unix:/var/run/php5-fpm.sock;
            fastcgi_index index.php;
            include fastcgi.conf;
    }

重新启动NGINX：

    sudo /etc/init.d/nginx reload

### 测试PHP

先将`index.html`改名为`index.php`：

    sudo mv /usr/share/nginx/www/index.html /usr/share/nginx/www/index.php

再编辑一下index.php的内容：

    sudo nano index.php

将里面的文本替换为：

    <?php echo phpinfo(); ?>

按下`Ctrl`和`X`后，按`Y`，再按`Enter`，保存修改后退出。这时刷新一下浏览器，应该可以看到PHP的版本以及其他设置信息。