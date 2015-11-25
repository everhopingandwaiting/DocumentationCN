---
ID: 398
post_title: 使用NOOBS前的准备——格式化SDXC卡
author: 有聰哥冇甩拖
post_date: 2015-10-26 17:33:18
post_excerpt: ""
layout: post
permalink: https://www.rpicn.org/documentation/installation/sdxc_formatting-md/
published: true
---
# 使用NOOBS前的准备——格式化SDXC卡

根据<a href="https://www.sdcard.org/developers/overview/capacity/" target="_blank">SD卡说明</a>容量超过32G的卡称为SDXC卡，并且需要格式化为exFAT格式。所以官方的格式化工具SD Formatter默认*只会*对64G或以上的SD卡格式化为exFAT格式。

树莓派的bootloader（即“引导程序”，内建在GPU中，无法升级）只支持从FAT（FAT16或FAT32）格式分区中读取，对exFAT格式就无能为力了。所以，如果希望在64G或更大的SD卡中使用NOOBS为树莓派安装系统，就需要事先将SD卡格式化为FAT32格式，然后再将NOOBS的文件复制进SD卡中。

## Linux和Mac OS系统

Linux和Mac OS系统自带的格式化工具就可以将SD卡格式化为FAT32（名称可能是FAT或MS-DOS）格式。只要删除了现有的exFAT格式的分区，再新建一个新的FAT32主分区，然后格式化，就可以按照[NOOBS使用说明](../noobs.md)继续进行系统安装了。

## Windows系统

官方的SD卡格式化工具SD Formatter对32G或以下的SD卡会格式化为FAT32格式，而对64G或以上的SD卡则会格式化为exFAT格式。如果使用的是64G或以上的SD卡，则需要用到其他的格式化工具了。有一款名为<a href="http://www.ridgecrop.demon.co.uk/guiformat.htm" target="_blank">FAT 32 Formatter</a>的工具可以做到，下载后只有单独一个文件，名为`guiformat.exe`，直接运行，无需安装。

首先运行<a href="https://www.sdcard.org/downloads/formatter_4/" target="_blank">SD Formatter</a>，“格式化选项”中的“逻辑大小调整”选择“ON”，这样可确保SD卡中所有的分区都会删除；格式化后，再使用FAT 32 Formatter（guiformat.exe），请确保盘符没选择错误，使用默认的设置即可，再点击“Start”开始格式化。完成后就可以按照[NOOBS使用说明](../noobs.md)继续进行系统安装了。

如果FAT 32 Formatter工具用起来不方便，也可以使用其他软件，例如<a href="http://www.minitool.com/partition-manager/partition-wizard-home.html" target="_blank">MiniTool Partition Wizard Free Edition</a>，又或者<a href="http://www.easeus.com/partition-manager/epm-free.html" target="_blank">EaseUS Partition Master Free</a>只要选择“Home User”，即“家用版”就可以免费获得具有完整功能 的分区软件使用许可。
