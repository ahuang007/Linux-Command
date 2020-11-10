# Linux ifconfig 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux ifconfig 命令用于显示或设置网络设备。

ifconfig 可设置网络设备的状态，或是显示目前的设置。

### 语法

```
ifconfig [网络设备][down up -allmulti -arp -promisc][add<地址>][del<地址>][<hw<网络设备类型><硬件地址>][io_addr<I/O地址>][irq<IRQ地址>][media<网络媒介类型>][mem_start<内存地址>][metric<数目>][mtu<字节>][netmask<子网掩码>][tunnel<地址>][-broadcast<地址>][-pointopoint<地址>][IP地址]
```

**参数说明**：

- add<地址> 设置网络设备IPv6的IP地址。
- del<地址> 删除网络设备IPv6的IP地址。
- down 关闭指定的网络设备。
- <hw<网络设备类型><硬件地址> 设置网络设备的类型与硬件地址。
- io_addr<I/O地址> 设置网络设备的I/O地址。
- irq<IRQ地址> 设置网络设备的IRQ。
- media<网络媒介类型> 设置网络设备的媒介类型。
- mem_start<内存地址> 设置网络设备在主内存所占用的起始地址。
- metric<数目> 指定在计算数据包的转送次数时，所要加上的数目。
- mtu<字节> 设置网络设备的MTU。
- netmask<子网掩码> 设置网络设备的子网掩码。
- tunnel<地址> 建立IPv4与IPv6之间的隧道通信地址。
- up 启动指定的网络设备。
- -broadcast<地址> 将要送往指定地址的数据包当成广播数据包来处理。
- -pointopoint<地址> 与指定地址的网络设备建立直接连线，此模式具有保密功能。
- -promisc 关闭或启动指定网络设备的promiscuous模式。
- [IP地址] 指定网络设备的IP地址。
- [网络设备] 指定网络设备的名称。

### 实例

显示网络设备信息

```
[root@localhost ~ ]$ ifconfig
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 0.0.0.0
        ether 02:42:c9:1d:18:09  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.9.90  netmask 255.255.248.0  broadcast 192.168.15.255
        inet6 fe80::853a:2399:2efa:62fa  prefixlen 64  scopeid 0x20<link>
        inet6 fe80::8708:9d2f:f426:aa04  prefixlen 64  scopeid 0x20<link>
        inet6 fe80::7fcb:47f8:9de7:388  prefixlen 64  scopeid 0x20<link>
        ether 00:15:5d:1d:5a:1b  txqueuelen 1000  (Ethernet)
        RX packets 40374035  bytes 12558938249 (11.6 GiB)
        RX errors 0  dropped 52364  overruns 0  frame 0
        TX packets 2386678  bytes 1576125137 (1.4 GiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 88162  bytes 202235464 (192.8 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 88162  bytes 202235464 (192.8 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

启动关闭指定网卡

```
[root@localhost ~ ]$ ifconfig eth0 down
[root@localhost ~ ]$ ifconfig eth0 up
```

为网卡配置和删除IPv6地址

```
[root@localhost ~ ]$ ifconfig eth0 add 33ffe:3240:800:1005::2/ 64 //为网卡设置IPv6地址

[root@localhost ~ ]$ ifconfig eth0 del 33ffe:3240:800:1005::2/ 64 //为网卡删除IPv6地址
```

用 ifconfig 修改 MAC 地址

```
[root@localhost ~ ]$ ifconfig eth0 down //关闭网卡
[root@localhost ~ ]$ ifconfig eth0 hw ether 00:AA:BB:CC:DD:EE //修改MAC地址
[root@localhost ~ ]$ ifconfig eth0 up //启动网卡
[root@localhost ~ ]$ ifconfig eth1 hw ether 00:1D:1C:1D:1E //关闭网卡并修改MAC地址 
[root@localhost ~ ]$ ifconfig eth1 up //启动网卡
```

配置IP地址

```
[root@localhost ~ ]$ ifconfig eth0 192.168.1.56 
//给eth0网卡配置IP地址
[root@localhost ~ ]$ ifconfig eth0 192.168.1.56 netmask 255.255.255.0 
// 给eth0网卡配置IP地址,并加上子掩码
[root@localhost ~ ]$ ifconfig eth0 192.168.1.56 netmask 255.255.255.0 broadcast 192.168.1.255
// 给eth0网卡配置IP地址,加上子掩码,加上个广播地址
```

启用和关闭ARP协议

```
[root@localhost ~ ]$ ifconfig eth0 arp  //开启
[root@localhost ~ ]$ ifconfig eth0 -arp  //关闭
```

设置最大传输单元

```
[root@localhost ~ ]$ ifconfig eth0 mtu 1500 
//设置能通过的最大数据包大小为 1500 bytes
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)