# Linux tcpdump 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux tcpdump 命令用于倾倒网络传输数据。

执行 tcpdump 指令可列出经过指定网络界面的数据包文件头，在 Linux 操作系统中，你必须是系统管理员。

### 语法

```
tcpdump [-adeflnNOpqStvx][-c<数据包数目>][-dd][-ddd][-F<表达文件>][-i<网络界面>][-r<数据包文件>][-s<数据包大小>][-tt][-T<数据包类型>][-vv][-w<数据包文件>][输出数据栏位]
```

**参数说明**：

- -a 尝试将网络和广播地址转换成名称。
- -c<数据包数目> 收到指定的数据包数目后，就停止进行倾倒操作。
- -d 把编译过的数据包编码转换成可阅读的格式，并倾倒到标准输出。
- -dd 把编译过的数据包编码转换成C语言的格式，并倾倒到标准输出。
- -ddd 把编译过的数据包编码转换成十进制数字的格式，并倾倒到标准输出。
- -e 在每列倾倒资料上显示连接层级的文件头。
- -f 用数字显示网际网络地址。
- -F<表达文件> 指定内含表达方式的文件。
- -i<网络界面> 使用指定的网络截面送出数据包。
- -l 使用标准输出列的缓冲区。
- -n 不把主机的网络地址转换成名字。
- -N 不列出域名。
- -O 不将数据包编码最佳化。
- -p 不让网络界面进入混杂模式。
- -q 快速输出，仅列出少数的传输协议信息。
- -r<数据包文件> 从指定的文件读取数据包数据。
- -s<数据包大小> 设置每个数据包的大小。
- -S 用绝对而非相对数值列出TCP关联数。
- -t 在每列倾倒资料上不显示时间戳记。
- -tt 在每列倾倒资料上显示未经格式化的时间戳记。
- -T<数据包类型> 强制将表达方式所指定的数据包转译成设置的数据包类型。
- -v 详细显示指令执行过程。
- -vv 更详细显示指令执行过程。
- -x 用十六进制字码列出数据包资料。
- -w<数据包文件> 把数据包数据写入指定的文件。

### 实例

显示TCP包信息

```
root@iZwz9ixqaqrvghd7vipsefZ:~# tcpdump
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
15:10:48.823061 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 1000933811:1000933919, ack 831554829, win 261, length 108
15:10:48.823085 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 108:144, ack 1, win 261, length 36
15:10:48.823105 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 144:252, ack 1, win 261, length 108
15:10:48.823119 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 252:288, ack 1, win 261, length 36
15:10:48.823382 IP iZwz9ixqaqrvghd7vipsefZ.38281 > 100.100.2.138.domain: 44247+ PTR? 138.226.110.113.in-addr.arpa. (46)
15:10:48.828039 IP 113.110.226.138.57722 > iZwz9ixqaqrvghd7vipsefZ.ssh: Flags [.], ack 288, win 1027, length 0
15:10:48.896497 IP 100.100.2.138.domain > iZwz9ixqaqrvghd7vipsefZ.38281: 44247 NXDomain 0/1/0 (134)
15:10:48.896917 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 504:660, ack 1, win 261, length 156
15:10:48.896955 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 696:860, ack 1, win 261, length 164
15:10:48.897003 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 896:1052, ack 1, win 261, length 156
15:10:48.897128 IP iZwz9ixqaqrvghd7vipsefZ.59225 > 100.100.2.136.domain: 61347+ PTR? 138.2.100.100.in-addr.arpa. (44)
15:10:48.897576 IP iZwz9ixqaqrvghd7vipsefZ.56389 > 100.100.2.138.domain: 17294+ PTR? 136.2.100.100.in-addr.arpa. (44)
15:10:48.897742 IP 100.100.2.138.domain > iZwz9ixqaqrvghd7vipsefZ.56389: 17294 NXDomain* 0/1/0 (99)
15:10:48.901694 IP 113.110.226.138.57722 > iZwz9ixqaqrvghd7vipsefZ.ssh: Flags [.], ack 504, win 1026, length 0
15:10:48.901725 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 1280:2800, ack 1, win 261, length 1520
......

1043 packets captured
1098 packets received by filter
55 packets dropped by kernel
```

显示指定数量包

```
root@iZwz9ixqaqrvghd7vipsefZ:~# tcpdump -c 20
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
15:11:48.117190 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 1001102591:1001102699, ack 831555657, win 261, length 108
15:11:48.117212 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 108:144, ack 1, win 261, length 36
15:11:48.117232 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 144:252, ack 1, win 261, length 108
15:11:48.117247 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 252:288, ack 1, win 261, length 36
15:11:48.117508 IP iZwz9ixqaqrvghd7vipsefZ.47379 > 100.100.2.138.domain: 11974+ PTR? 138.226.110.113.in-addr.arpa. (46)
15:11:48.117719 IP 100.100.2.138.domain > iZwz9ixqaqrvghd7vipsefZ.47379: 11974 NXDomain 0/1/0 (134)
15:11:48.117843 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 288:468, ack 1, win 261, length 180
15:11:48.117901 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 504:660, ack 1, win 261, length 156
15:11:48.117951 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 696:860, ack 1, win 261, length 164
15:11:48.118052 IP iZwz9ixqaqrvghd7vipsefZ.45598 > 100.100.2.136.domain: 47892+ PTR? 138.2.100.100.in-addr.arpa. (44)
15:11:48.118323 IP 100.100.2.136.domain > iZwz9ixqaqrvghd7vipsefZ.45598: 47892 NXDomain* 0/1/0 (99)
15:11:48.118621 IP iZwz9ixqaqrvghd7vipsefZ.53910 > 100.100.2.138.domain: 15881+ PTR? 136.2.100.100.in-addr.arpa. (44)
15:11:48.118724 IP 100.100.2.138.domain > iZwz9ixqaqrvghd7vipsefZ.53910: 15881 NXDomain* 0/1/0 (99)
15:11:48.121751 IP 113.110.226.138.57722 > iZwz9ixqaqrvghd7vipsefZ.ssh: Flags [.], ack 288, win 1024, length 0
15:11:48.121770 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 860:2792, ack 1, win 261, length 1932
15:11:48.121816 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 2792:2940, ack 1, win 261, length 148
15:11:48.121843 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 2940:2976, ack 1, win 261, length 36
15:11:48.121876 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 2976:3140, ack 1, win 261, length 164
15:11:48.121895 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 3140:3176, ack 1, win 261, length 36
15:11:48.121922 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: Flags [P.], seq 3176:3340, ack 1, win 261, length 164
20 packets captured
25 packets received by filter
2 packets dropped by kernel
```

精简显示

```
root@iZwz9ixqaqrvghd7vipsefZ:~# tcpdump -c 10 -q
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
15:12:05.708608 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: tcp 108
15:12:05.708646 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: tcp 36
15:12:05.708670 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: tcp 108
15:12:05.708684 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: tcp 36
15:12:05.708932 IP iZwz9ixqaqrvghd7vipsefZ.34755 > 100.100.2.138.domain: UDP, length 46
15:12:05.709186 IP 100.100.2.138.domain > iZwz9ixqaqrvghd7vipsefZ.34755: UDP, length 134
15:12:05.709306 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: tcp 116
15:12:05.709359 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: tcp 116
15:12:05.709394 IP iZwz9ixqaqrvghd7vipsefZ.ssh > 113.110.226.138.57722: tcp 116
15:12:05.709471 IP iZwz9ixqaqrvghd7vipsefZ.43532 > 100.100.2.136.domain: UDP, length 44
10 packets captured
15 packets received by filter
2 packets dropped by kernel
```

转换可阅读格式

```
root@iZwz9ixqaqrvghd7vipsefZ:~# tcpdump -d
(000) ret      #262144
```

转换成十进制格式

```
root@iZwz9ixqaqrvghd7vipsefZ:~# tcpdump -ddd
1
6 0 0 262144
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)