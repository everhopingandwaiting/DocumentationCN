---
ID: 132
post_title: raspi-config
author:
  - adm
post_date:
  - 2015-10-19 23:54:55
post_excerpt:
  - ""
layout: post
permalink:
  - ""
published: true
---
# raspi-config

`raspi-config`是由[Alex Bradbury](https://github.com/asb)编写并维护的树莓派设置工具，特别为Raspbian度身订造。

## 用法

第一次运行Raspbian时，系统会提醒用户运行`raspi-config`。要开始使用这个工具，只需要在终端输入这个命令：

```
sudo raspi-config
```

`sudo`意思是临时以超级用户执行后面的命令，因当前用户`pi`可能不具备修改一些特别文件的权限。

随后终端将显示一个蓝色的屏幕，还有一个列满各种选项的灰色框框，如下图所示：

![raspi-config main screen](https://github.com/raspberrypi/documentation/blob/master/configuration/images/raspi-config.png)

工具提供的选项包括：

`                        Raspberry Pi Software Configuration Tool (raspi-config)`
` `
`Setup Options`
` `
`    1 Expand Filesystem              Ensures that all of the SD card storage is available to the OS`
`    2 Change User Password           Change password for the default user (pi)`
`    3 Enable Boot to Desktop/Scratch Choose whether to boot into a desktop environment, Scratch, or the command line`
`    4 Internationalisation Options   Set up language and regional settings to match your location`
`    5 Enable Camera                  Enable this Pi to work with the Raspberry Pi Camera`
`    6 Add to Rastrack                Add this Pi to the online Raspberry Pi Map (Rastrack)`
`    7 Overclock                      Configure overclocking for your Pi`
`    8 Advanced Options               Configure advanced settings`
`    9 About raspi-config           Information about this configuration tool`
` `
`                                   <Select>                                  <Finish>`

### 在菜单中移动光标

在各个选项中，可以使用上下箭头键高亮显示各种选项。按下右箭头会跳到“选择”和“完成”按钮，按下左箭头则返回选项列表。此外，还可以使用“Tab”键切换这两个区域。

另外值得一提的是，假如选项列表非常长，比如“时区”列表，用户可以按字母键快速跳到相应的部分。例如，按下“L”键，列表将显示以“L”开头的第一个选项“Lisbon”，距离“London”只剩下两行，大大节省用户滚动列表的时间。

### `raspi-config`的任务是什么

`raspi-config`程序为常用设置的更改提供了便捷的途径。这个工具可能会更改`/boot/config.txt`或其他不同的Linux设置文件。有些选项可能需要重启方能生效，假如用户作了需要重启的改动，按下“完成”键退出`raspi-config`后，程序会提示询问用户是否重启。

## 菜单选项

### Expand filesystem（扩展文件系统）

如果Raspbian是使用NOOBS安装的，这个选项可以跳过，因NOOBS会自动扩展文件系统。但是如果用户自行使用系统镜像安装系统，则需要应用该选项，因为SD卡的系统分区会剩下3G左右未使用的空间。应用该选项后重启后生效，SD卡剩余的空间将可以全部使用。注意，该选项应用时并不需要确认，将会即时执行文件系统的扩展。

### Change user password（更改用户密码）

树莓派默认用户是`pi`，其密码是`raspberry`。在这里可以更改用户密码。参考[用户](../linux/usage/users.md)可了解更多关于用户的设置。

### Enable boot to desktop or Scratch（开机自动进入桌面或Scratch）

树莓派开机后进入命令行界面、图形界面抑或直接到Scratch，可以在这里更改。

### Internationalisation options（区域和语言）





### Internationalisation options

Select `Internationalisation Options` and hit `Enter` to be taken to a sub-menu containing the following options:

<a name="change-locale"></a>
#### Change locale

Select a locale, for example `en_GB.UTF-8 UTF-8`.

<a name="change-timezone"></a>
#### Change timezone

Select your local timezone, starting with the region such as `Europe`; then select a city, for example `London`. Type a letter to skip down the list to that point in the alphabet.

<a name="change-keyboard-layout"></a>
#### Change keyboard layout

This option opens another menu which allows you to select your keyboard layout. It will take a long time to display while it reads all the keyboard types. Changes usually take effect immediately, but may require a reboot.

<a name="enable-camera"></a>
### Enable camera

In order to use the Raspberry Pi camera module, you must enable it here. Select the option and proceed to `Enable`. This will make sure at least 128MB of RAM is dedicated to the GPU.

<a name="add-to-rastrack"></a>
### Add to Rastrack

Rastrack is a user-contributed Google Map to which Pi users in the community have added their location; it shows a heat map of where Pi users are known to be around the world. This was set up by young Pi enthusiast [Ryan Walmsley](http://ryanteck.uk/) in 2012. Rastrack is located at [rastrack.co.uk](http://rastrack.co.uk/).

You can use this option to add your location to the map.

<a name="overclock"></a>
### Overclock

It is possible to overclock your Raspberry Pi's CPU. The default is 700MHz but it can be set up to 1000MHz. The overclocking you can achieve will vary; overclocking too high may result in instability. Selecting this option shows the following warning:

```
Be aware that overclocking may reduce the lifetime of your Raspberry Pi. If overclocking at a certain level causes system instability, try a more modest overclock. Hold down `shift` during boot to temporarily disable overclock.
```

### Advanced options

<a name="overscan"></a>
#### Overscan

Old TV sets had a significant variation in the size of the picture they produced; some had cabinets that overlapped the screen. TV pictures were therefore given a black border so that none of the picture was lost; this is called overscan. Modern TVs and monitors don't need the border, and the signal doesn't allow for it. If the initial text shown on the screen disappears off the edge, you need to enable overscan to bring the border back.

Any changes will take effect after a reboot. You can have greater control over the settings by editing [config.txt](config-txt.md).

On some displays, particularly monitors, disabling overscan will make the picture fill the whole screen and correct the resolution. For other displays, it may be necessary to leave overscan enabled and adjust its values.

<a name="hostname"></a>
#### Hostname

Set the visible name for this Pi on a network.

<a name="memory-split"></a>
#### Memory split

Change the amount of memory made available to the GPU.

<a name="ssh"></a>
#### SSH

Enable/disable remote command line access to your Pi using SSH.

SSH allows you to remotely access the command line of the Raspberry Pi from another computer. Disabling this ensures the SSH service does not start on boot, freeing up processing resources. Read more about using [SSH](../remote-access/ssh/README.md). Note that SSH is enabled by default. If connecting your Pi directly to a public network, you should disable SSH unless you have set up secure passwords for all users.

<a name="device-tree"></a>
#### Device Tree

Enable/Disable the use of Device Tree. Read more about [Device Trees Config](device-tree.md).

<a name="spi"></a>
#### SPI

Enable/Disable SPI interfaces and automatic loading of SPI kernel module, needed for products such as PiFace.

<a name="i2c"></a>
#### I2C

Enable/Disable I2C interfaces and automatic loading of I2C kernel module.

<a name="serial"></a>
#### Serial

Enable/Disable shell and kernel messages on the serial connection.

<a name="audio"></a>
#### Audio

Force audio out through HDMI or a 3.5mm jack. Read more about [audio configuration](audio-config.md).

<a name="update"></a>
#### Update

Update this tool to the latest version.

<a name="about"></a>
### About raspi-config

Selecting this option shows the following text:

```
This tool provides a straight-forward way of doing initial configuration of the Raspberry Pi. Although it can be run at any time, some of the options may have difficulties if you have heavily customised your installation.
```

<a name="finish"></a>
### Finish

Use this button when you have completed your changes. You will be asked whether you want to reboot or not. When used for the first time it's best to reboot. There will be a delay in rebooting if you have chosen to resize your SD card.

## Development of this tool

See this tool's source at [github.com/asb/raspi-config](https://github.com/asb/raspi-config), where you can open issues and create pull requests.

---

*This article uses content from the eLinux wiki page [RPi raspi-config](http://elinux.org/RPi_raspi-config), which is shared under the [Creative Commons Attribution-ShareAlike 3.0 Unported license](http://creativecommons.org/licenses/by-sa/3.0/)*

