---
ID: 41
post_title: SD卡（TF卡）
author: adm
post_date: 2015-10-16 12:25:16
post_excerpt: ""
layout: post
permalink: >
  https://www.rpicn.org/uncategorized/sd-cards-md/
published: true
---
# SD卡（TF卡）

一般情况下，树莓派可使用SD标准的存储卡，但请注意下列指引：

- SD卡容量。若使用NOOBS安装系统，建议使用8G以上的SD卡；若使用其他镜像安装系统，建议使用4G以上的SD卡;某些发行版可安装在更小的SD卡中，比如OpenElec和Arch。

- SD卡类型。SD卡协会定义了SD卡的几种速度规格，可令用户直观地区分不同类型SD卡的数据读写速率。比如Class 4（C4）的写入速率应达到4MB/s，而C10应达10MB/s。但这并非表示日常使用中C10与C4的卡相比更胜一筹，因为写入速度的提升往往需要牺牲读取速度及增加寻道时间。

官方建议购买8G、C6的[Raspberry Pi TF card](http://swag.raspberrypi.org/products/noobs-8gb-sd-card)，据称这张卡“秒杀”市面上其余的SD卡，更附送一张SD卡套，十分超值。

译者注：SD卡（TF卡）的兼容情况，可参考[elinux.org](http://elinux.org)的这个Wiki：[RPi SD cards](http://elinux.org/RPi_SD_cards)。

若遇到SD卡数据损坏的问题，请确保遵循以下事项：

1. 确保使用的是正品SD卡。市面上有廉价的“扩容卡”，不仅容量比卖家声称的小，而且使用寿命有限。
2. 确保使用优质的电源适配器。可以通过测量树莓派TP1和TP2针脚之间的电压检测；如果高负荷情况下，此电压低于4.75V，请勿再使用此电源适配器。
3. 确保使用优质的USB线缆供电。出于成本控制，普通的USB线缆尽可能少地使用铜芯，这种线缆的内阻可能会使TP1->TP2两脚之间的电压低于4.75V，因此耗损的电源可能高达1V或更甚！
4. 确保正确关机后再切断电源。输入`sudo halt`后再稍等片刻，待LED指示灯提示方可断电。（译者注：2代B型为绿灯停止闪烁后才可断电）。
5. 超频可能引致数据损坏！该问题已被修复，但即便如此，该问题仍有可能发生。

若按上述事项得以确保后仍然出现数据损坏的问题，请告知我们，谢谢！
