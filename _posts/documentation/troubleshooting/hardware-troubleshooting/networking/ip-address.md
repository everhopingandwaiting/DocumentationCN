# IP地址

树莓派默认开启了DHCP客户端，如果树莓派通过网线连接到开启了DHCP服务的路由，将会自动获取到IP地址。

如果需要通过[SSH](../../../../remote-access/ssh/README.md.16)或者[VNC](../../../../remote-access/vnc/README.md.3)连接到树莓派，必须事先知道树莓派的IP地址。对于连接了显示器的树莓派来说很容易，而对于没连接显示器的树莓派来说也有不少的方法。

## 有显示器的树莓派

- 如果开机使用命令行界面，屏幕上的命令行提示符的上面几行会自动显示树莓派本机的IP地址。
- 万一在命令行界面玩得太欢乐忘记了，在命令行中输入`hostname -I`，系统就会显示IP地址了。
- 又或者进入了图形界面，打开LXTerminal，同样地输入`hostname -I`吧！

## 没显示器的树莓派

下面几种方法，适用于局域网内没连接显示器的树莓派：

### 路由器Web管理页面

在浏览器中输入路由器的管理页面。通常路由器在背面的铭牌上印有Web管理地址，还有登录用户名及密码，例如：`http://192.168.1.1`，等等。再找到“客户端列表”（或者类似的名称，各个品牌的路由器用的名字可能会有不同，反正就是“局域网内的机器”的意思），应该能看到一些设备的列表，在设备名称一栏寻找“Raspberry Pi Foundation”，又或者是树莓派的默认主机名“raspberrypi”，这样就可以找到相应的IP地址了。

### nmap命令

`nmap`命令（Network Mapper）是一个开源的工具，用来寻找“网路上的芳邻”。Linux，Mac OS，或Windows平台上都有相应的版本。

- **Linux**版本的安装，输入`sudo apt-get install nmap`；
- **Mac OS**或**Windows**版本的安装，请前往<a href="http://nmap.org/download.html" target="_blank">nmap.org</a>；

要使用`nmap`扫描局域网内的设备，需要事先知道所连接到的具体网段。这样需要先找到本机的IP地址：

- 对于**Linux**或**Mac OS**系统，只需要在终端中输入`hostname -I`；
- 在**Mac OS**系统还可以在“设置”，“网络”中找到本机的IP地址；
- 在**Windows**系统中，需要前往“控制面板”，“网络和共享中心”，点击“本地连接”，再在弹出的“本地连接状态”窗口中点击“详细信息”；

取得本机的IP地址后，就可以扫描整个本地网络寻找其他设备了。例如，如果本机地址是`192.168.1.5`，其他设备的IP地址应该是`192.168.1.x`，这个x可能是2、3、4、6……一直到255。这个网段的标识符写法是这样的：`192.168.1.0/24`。

然后用`nmap`命令，加上`-sn`参数（只用ping），扫描整个网段，可能需时较长，整句命令如下：

    nmap -sn 192.168.1.0/24

仅仅使用ping来扫描可以节省时间，如果特定的IP地址设备有响应可以马上显示，例如：

    Starting Nmap 6.40 ( http://nmap.org ) at 2014-03-10 12:46 GMT
    Nmap scan report for hpprinter (192.168.1.2)
    Host is up (0.00044s latency).
    Nmap scan report for Gordons-MBP (192.168.1.4)
    Host is up (0.0010s latency).
    Nmap scan report for ubuntu (192.168.1.5)
    Host is up (0.0010s latency).
    Nmap scan report for raspberrypi (192.168.1.8)
    Host is up (0.0030s latency).
    Nmap done: 256 IP addresses (4 hosts up) scanned in 2.41 seconds

上面的结果显示，主机名为`raspberrypi`的设备，IP地址为`192.168.1.8`。

### 其他工具

可以使用<a href="https://github.com/j-keck/lsleases" target="_blank">lsleases</a>。
