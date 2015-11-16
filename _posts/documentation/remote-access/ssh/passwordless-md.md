---
ID: 318
post_title: 免密码SSH登陆
author: 有聰哥冇甩拖
post_date: 2015-10-26 13:36:27
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/remote-access/ssh/passwordless-md/
published: true
---
# 免密码SSH登陆

如果使用SSH的公、私密钥配对，用户可以不必每次输入密码登入树莓派。

## 先检查现有的SSH密钥

首先检查本地电脑是否存在密钥：

`ls ~/.ssh`

如果找到名为`id_rsa.pub`或`id_dsa.pub`，说明本地电脑中已有密钥，可先跳过下面“生成密钥”这步（当然也可以先用`rm id*`这个命令删除后继续“生成密钥”）。

## 生成密钥

输入以下命令生成密钥（建议使用主机名用作识别，如`<YourName>@<YourDevice>`，本文所举例子使用`eben@pi`）：

`ssh-keygen -t rsa -C eben@pi`








You can also use a more descriptive comment using quotes if you have spaces, e.g. `ssh-keygen -t rsa -C "Raspberry Pi #123"`

Upon entering this command, you'll be asked where to save the key. We suggest you save it in the default location (`/home/pi/.ssh/id_rsa`) by just hitting `Enter`.

You'll also be asked to enter a passphrase. This is extra security which will make the key unusable without your passphrase, so if someone else copied your key, they could not impersonate you to gain access. If you choose to use a passphrase, type it here and press `Enter`, then type it again when prompted. Leave empty for no passphrase.

Now you should see the files `id_rsa` and `id_rsa.pub` in your `.ssh` directory in your home folder:

```
ls ~/.ssh
```

```
authorized_keys  id_rsa  id_rsa.pub  known_hosts
```

The `id_rsa` file is your private key. Keep this on your computer.

The `id_rsa.pub` file is your public key. This is what you put on machines you want to connect to. When the machine you try to connect to matches up your public and private key, it will allow you to connect.

Take a look at your public key to see what it looks like:

```
cat ~/.ssh/id_rsa.pub
```

It should be in the form:

```
ssh-rsa <REALLY LONG STRING OF RANDOM CHARACTERS> eben@pi
```

## Copy your public key to your Raspberry Pi

To copy your public key to your Raspberry Pi, use the following command to append the public key to your `authorized_keys` file on the Pi, sending it over SSH:

```
cat ~/.ssh/id_rsa.pub | ssh <USERNAME>@<IP-ADDRESS> 'cat >> .ssh/authorized_keys'
```

Note that this time you will have to authenticate with your password.

Now try `ssh <USER>@<IP-ADDRESS>` and you should connect without a password prompt.

If you see a message "Agent admitted failure to sign using the key." then add your RSA or DSA identities to the authentication agent, ssh-agent 
the execute the following command:  
```
ssh-add
```

If this did not work, delete your keys with `rm ~/.ssh/id*` and follow the instructions again.

You can also send files over SSH using the `scp` command (secure copy). See the [SCP guide](../scp.md) for more information.
