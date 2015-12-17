---
ID: 318
post_title: 免密码SSH登陆
author: 有聰哥冇甩拖
post_date: 2015-10-26 13:36:27
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/ssh/passwordless-md/
published: true
_theme_show_post_title: 0
---
# 免密码SSH登陆

如果使用SSH的公、私密钥配对，用户可以不必每次输入密码登入树莓派。

## 先检查现有的SSH密钥

首先检查本地电脑是否存在密钥：

    ls ~/.ssh

如果找到名为`id_rsa.pub`或`id_dsa.pub`，说明本地电脑中已有密钥，可先跳过下面“生成密钥”这步（当然也可以先用`rm id*`这个命令删除后继续“生成密钥”）。

## 生成密钥

输入以下命令生成密钥（建议使用主机名用作识别，如`<YourName>@<YourDevice>`，本文所举例子使用`eben@pi`）：

    ssh-keygen -t rsa -C eben@pi

用户可以使用引号以不同的名称用于区分，例如`ssh-keygen -t rsa -C "Raspberry Pi #123"`。

输入这个命令后，用户会被提示保存密钥。建议按下`Enter`确认保存在默认路径（`/home/pi/.ssh/id_rsa`）。

用户还会被要求输入另外一个密码短语，这个密码短语是用来保护用户私钥的，确保不被盗用。如果需要使用密码短语，输入完成后按下`Enter`，然后再输入一次密码短语确认。如果不需要使用密码短语，可以选择不输入。

这时，输入下面这个命令，应该可以在`.ssh`目录下查找到`id_rsa`和`id_rsa.pub`：

    ls ~/.ssh

    authorized_keys  id_rsa  id_rsa.pub  known_hosts

`id_rsa`文件就是用户的私钥，需要保存在本地电脑上。

`id_rsa.pub`是公钥，需要保存在远端电脑上。当用户在本地发出连接请求时，远端电脑会校验用户的私钥，通过验证后就允许用户远程连接了。

可以用下面这条命令打开密钥，看看它长什么样子：

    cat ~/.ssh/id_rsa.pub

如无意外，终端会显示：

    ssh-rsa <这堆乱码人类应该无法短时间内破译> eben@pi

## 将公钥复制到树莓派中

使用下面的命令就可以通过SSH将`authorized_keys`文件追加到树莓派上去就可以加入公钥了：

    cat ~/.ssh/id_rsa.pub | ssh <USERNAME>@<IP-ADDRESS> 'cat >> .ssh/authorized_keys'

请注意，这时还需要输入一次密码。

以后再输入`ssh <USERNAME>@<IP-ADDRESS>`命令后，就可以不用再输入密码了。

如果系统提示`Agent admitted failure to sign using the key.`，这时需要将RSA或DSA数字证书添加到校验代理`ssh-agent`去，使用以下命令即可：

    ssh-add


如果不成功，可以用这条命令`rm ~/.ssh/id*`删除所以密钥再重新按本文所述步骤再次尝试。

另外，用户也可以使用`scp`命令通过SSH连接将文件复制到远程的电脑上去，详细请参考[SCP指引](../scp.md)。
