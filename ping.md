# Linux ping 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux ping 命令用于检测主机。

执行 ping 指令会使用 ICMP 传输协议，发出要求回应的信息，若远端主机的网络功能没有问题，就会回应该信息，因而得知该主机运作正常。

### 语法

```
ping [-dfnqrRv][-c<完成次数>][-i<间隔秒数>][-I<网络界面>][-l<前置载入>][-p<范本样式>][-s<数据包大小>][-t<存活数值>][主机名称或IP地址]
```

**参数说明**：

- -d 使用Socket的SO_DEBUG功能。
- -c<完成次数> 设置完成要求回应的次数。
- -f 极限检测。
- -i<间隔秒数> 指定收发信息的间隔时间。
- -I<网络界面> 使用指定的网络接口送出数据包。
- -l<前置载入> 设置在送出要求信息之前，先行发出的数据包。
- -n 只输出数值。
- -p<范本样式> 设置填满数据包的范本样式。
- -q 不显示指令执行过程，开头和结尾的相关信息除外。
- -r 忽略普通的Routing Table，直接将数据包送到远端主机上。
- -R 记录路由过程。
- -s<数据包大小> 设置数据包的大小。
- -t<存活数值> 设置存活数值TTL的大小。
- -v 详细显示指令的执行过程。

### 实例

检测是否与主机连通

```
[huanglijun@localhost ~]$ ping www.baidu.com
PING www.a.shifen.com (14.215.177.38) 56(84) bytes of data.
64 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=1 ttl=55 time=7.43 ms
64 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=2 ttl=55 time=6.75 ms
64 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=3 ttl=55 time=6.75 ms
64 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=4 ttl=55 time=7.09 ms
64 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=5 ttl=55 time=6.91 ms
64 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=6 ttl=55 time=7.42 ms
64 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=7 ttl=55 time=6.79 ms
64 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=8 ttl=55 time=7.90 ms
64 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=9 ttl=55 time=6.27 ms
^C
--- www.a.shifen.com ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 8009ms
rtt min/avg/max/mdev = 6.277/7.039/7.901/0.462 ms

//需要手动终止Ctrl+C
```

指定接收包的次数

```
[huanglijun@localhost ~]$ ping -c 2 www.baidu.com
PING www.a.shifen.com (14.215.177.38) 56(84) bytes of data.
64 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=1 ttl=55 time=6.69 ms
64 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=2 ttl=55 time=7.36 ms

--- www.a.shifen.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 6.692/7.028/7.364/0.336 ms

//收到两次包后，自动退出
```

多参数使用

```
[huanglijun@localhost ~]$ ping -i 3 -s 1024 -t 255 www.baidu.com
PING www.a.shifen.com (14.215.177.38) 1024(1052) bytes of data.
1032 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=1 ttl=55 time=7.39 ms
1032 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=2 ttl=55 time=7.75 ms
1032 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=3 ttl=55 time=6.88 ms
1032 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=4 ttl=55 time=6.85 ms
1032 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=5 ttl=55 time=7.47 ms
1032 bytes from 14.215.177.38 (14.215.177.38): icmp_seq=6 ttl=55 time=6.92 ms
^C
--- www.a.shifen.com ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 15017ms
rtt min/avg/max/mdev = 6.856/7.214/7.752/0.357 ms

//-i 3 发送周期为 3秒 -s 设置发送包的大小 -t 设置TTL值为 255
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)