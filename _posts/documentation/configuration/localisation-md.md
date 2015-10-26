---
ID: 295
post_title: 本地化
author: adm
post_date: 2015-10-25 23:08:32
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/configuration/localisation-md/
published: true
---
# 本地化

使树莓派的本地化设置。

## 更改语言

### NOOBS

使用NOOBS安装系统的时候，用户可按下字母键`L`后，用上下箭头选中合适的语言，再按下`Enter`选定；当然也可以使用鼠标选择。NOOBS会记下用户的选择，以后将会显示已选定的语言。

另外，使用NOOBS安装系统的话，也可以参考[这篇文章](https://github.com/raspberrypi/noobs/blob/master/README.md#how-to-change-the-default-language-keyboard-layout-display-mode-or-boot-partition)，在安装系统之前预先设定。

### Raspbian

如果已经使用NOOBS完成了Raspbian的安装，Raspbian会按照NOOBS的设定选择相应的语言。但如果用户希望选择另一种显示语言，或系统是使用系统镜像安装的Raspbian，可以使用[raspi-config](../raspi-config.md)。


## 更改键盘布局

### NOOBS

使用NOOBS安装系统的时候，用户可以按下数字键`9`后，用上下箭头选中合适的布局，再按下`Enter`选定；当然也可以使用鼠标选择。NOOBS会记下用户的选择，以后将会使用已选定的键盘布局。

另外，使用NOOBS安装系统的话，也可以参考[这篇文章](https://github.com/raspberrypi/noobs/blob/master/README.md#how-to-change-the-default-language-keyboard-layout-display-mode-or-boot-partition)，在安装系统之前预先设定。

### Raspbian

如果已经使用NOOBS完成了Raspbian的安装，Raspbian会按照NOOBS的设定选择相应的键盘布局。但如果用户希望选择另一种键盘布局，或系统是使用系统镜像安装的Raspbian，可以使用[raspi-config](../raspi-config.md)。


## 更改时区

### NOOBS

时区设置对于NOOBS并非必不可少的，因此并未提供更改时区的选项。

### Raspbian

还是需要 [raspi-config](../raspi-config.md)出马。
