# Linux netstat 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux netstat 命令用于显示网络状态。

利用 netstat 指令可让你得知整个 Linux 系统的网络情况。

### 语法

```
netstat [-acCeFghilMnNoprstuvVwx][-A<网络类型>][--ip]
```

**参数说明**：

- -a或--all 显示所有连线中的Socket。
- -A<网络类型>或--<网络类型> 列出该网络类型连线中的相关地址。
- -c或--continuous 持续列出网络状态。
- -C或--cache 显示路由器配置的快取信息。
- -e或--extend 显示网络其他相关信息。
- -F或--fib 显示FIB。
- -g或--groups 显示多重广播功能群组组员名单。
- -h或--help 在线帮助。
- -i或--interfaces 显示网络界面信息表单。
- -l或--listening 显示监控中的服务器的Socket。
- -M或--masquerade 显示伪装的网络连线。
- -n或--numeric 直接使用IP地址，而不通过域名服务器。
- -N或--netlink或--symbolic 显示网络硬件外围设备的符号连接名称。
- -o或--timers 显示计时器。
- -p或--programs 显示正在使用Socket的程序识别码和程序名称。
- -r或--route 显示Routing Table。
- -s或--statistice 显示网络工作信息统计表。
- -t或--tcp 显示TCP传输协议的连线状况。
- -u或--udp 显示UDP传输协议的连线状况。
- -v或--verbose 显示指令执行过程。
- -V或--version 显示版本信息。
- -w或--raw 显示RAW传输协议的连线状况。
- -x或--unix 此参数的效果和指定"-A unix"参数相同。
- --ip或--inet 此参数的效果和指定"-A inet"参数相同。

### 实例

显示详细的网络状况

```
[root@localhost log (dev)]$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:11351           0.0.0.0:*               LISTEN     
tcp        0      0 localhost:ipp           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:rsms            0.0.0.0:*               LISTEN     
tcp        0      0 localhost:6011          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:11452           0.0.0.0:*               LISTEN 
...
```

显示当前户籍UDP连接状况

```
[root@localhost log (dev)]$ netstat -nu
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State 
```

显示UDP端口号的使用情况

```
[root@localhost log (dev)]$ netstat -apu
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name    
udp        0      0 localhost.locald:domain 0.0.0.0:*                           2218/dnsmasq        
udp        0      0 0.0.0.0:bootps          0.0.0.0:*                           2218/dnsmasq        
udp        0      0 0.0.0.0:sunrpc          0.0.0.0:*                           1/systemd           
udp        0      0 0.0.0.0:mdns            0.0.0.0:*                           974/avahi-daemon: r 
udp        0      0 localhost:323           0.0.0.0:*                           995/chronyd         
udp        0      0 0.0.0.0:44485           0.0.0.0:*                           974/avahi-daemon: r 
udp        0      0 0.0.0.0:723             0.0.0.0:*                           981/rpcbind         
udp6       0      0 [::]:sunrpc             [::]:*                              1/systemd           
udp6       0      0 localhost:323           [::]:*                              995/chronyd         
udp6       0      0 [::]:723                [::]:*                              981/rpcbind 
```

显示网卡列表

```
[root@localhost log (dev)]$ netstat -i  
Kernel Interface table
Iface             MTU    RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0             1500 59984611      0      5 0      13696757      0      0      0 BMRU
lo              65536  4912555      0      0 0       4912555      0      0      0 LRU
virbr0           1500        0      0      0 0             0      0      0      0 BMU
```

显示组播组的关系

```
[root@localhost log (dev)]$ netstat -g
IPv6/IPv4 Group Memberships
Interface       RefCnt Group
--------------- ------ ---------------------
lo              1      all-systems.mcast.net
eth0            1      224.0.0.251
eth0            1      all-systems.mcast.net
virbr0          1      224.0.0.251
virbr0          1      all-systems.mcast.net
lo              1      ip6-allnodes.lan
lo              1      ff01::1
eth0            1      ff02::1:fff8:20d9
eth0            1      ip6-allnodes.lan
eth0            1      ff01::1
virbr0          1      ip6-allnodes.lan
virbr0          1      ff01::1
virbr0-nic      1      ip6-allnodes.lan
virbr0-nic      1      ff01::1
```

显示网络统计信息

```
[root@localhost log (dev)]$ netstat -s
Ip:
    42949247 total packets received
    0 forwarded
    0 incoming packets discarded
    40345726 incoming packets delivered
    18593212 requests sent out
    14 outgoing packets dropped
    222 dropped because of missing route
    10 reassemblies required
    2 packets reassembled ok
Icmp:
    363 ICMP messages received
    84 input ICMP message failed.
    ICMP input histogram:
        destination unreachable: 353
        echo requests: 8
        echo replies: 2
    391 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
        destination unreachable: 378
        echo request: 5
        echo replies: 8
IcmpMsg:
        InType0: 2
        InType3: 353
        InType8: 8
        OutType0: 8
        OutType3: 378
        OutType8: 5
Tcp:
    6822 active connections openings
    2510 passive connection openings
    2700 failed connection attempts
    4055 connection resets received
    65 connections established
    19447886 segments received
    46035976 segments send out
    5106 segments retransmited
    0 bad segments received.
    4535 resets sent
Udp:
    20182751 packets received
    98 packets to unknown port received.
    0 packet receive errors
    5023 packets sent
    0 receive buffer errors
    0 send buffer errors
UdpLite:
TcpExt:
    191 invalid SYN cookies received
    1521 TCP sockets finished time wait in fast timer
    135903 delayed acks sent
    9 delayed acks further delayed because of locked socket
    Quick ack mode was activated 12 times
    215 packets directly queued to recvmsg prequeue.
    99290 bytes directly received in process context from prequeue
    8490054 packet headers predicted
    126 packets header predicted and directly queued to user
    2185960 acknowledgments not containing data payload received
    4720661 predicted acknowledgments
    19 times recovered from packet loss by selective acknowledgements
    1 congestion windows recovered without slow start by DSACK
    482 fast retransmits
    2 forward retransmits
    447 other TCP timeouts
    TCPLossProbes: 1764
    TCPLossProbeRecovery: 948
    18 DSACKs sent for old packets
    1335 DSACKs received
    2151 connections reset due to unexpected data
    24 connections reset due to early user close
    401 connections aborted due to timeout
    TCPDSACKIgnoredNoUndo: 936
    TCPSackShifted: 71
    TCPSackMerged: 33
    TCPSackShiftFallback: 173
    IPReversePathFilter: 3
    TCPRetransFail: 1
    TCPRcvCoalesce: 1728076
    TCPOFOQueue: 1082
    TCPChallengeACK: 23
    TCPSpuriousRtxHostQueues: 130
    TCPAutoCorking: 43
    TCPFromZeroWindowAdv: 146
    TCPToZeroWindowAdv: 146
    TCPWantZeroWindowAdv: 877
    TCPSynRetrans: 95
    TCPOrigDataSent: 41356980
    TCPHystartTrainDetect: 77
    TCPHystartTrainCwnd: 4757
    TCPACKSkippedSeq: 689
IpExt:
    InNoRoutes: 83
    InMcastPkts: 20397762
    OutMcastPkts: 521
    InBcastPkts: 725795
    InOctets: 8824122336
    OutOctets: 44502917996
    InMcastOctets: 4580624950
    OutMcastOctets: 89923
    InBcastOctets: 107972359
    InNoECTPkts: 44060415
    InECT0Pkts: 109

```

显示监听的套接口

```
[root@localhost log (dev)]$ netstat -l
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:11351           0.0.0.0:*               LISTEN     
tcp        0      0 localhost:ipp           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:rsms            0.0.0.0:*               LISTEN     
tcp        0      0 localhost:6011          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:11452           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10301           0.0.0.0:*               LISTEN     
tcp        0      0 localhost:6013          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10400           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10304           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:zabbix-trapper  0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10052           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:11301           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10151           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10154           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:11051           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10251           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:11052           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:11151           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:sunrpc          0.0.0.0:*               LISTEN     
tcp        0      0 localhost.locald:domain 0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:ssh             0.0.0.0:*               LISTEN     
tcp6       0      0 localhost:ipp           [::]:*                  LISTEN     
tcp6       0      0 localhost:6011          [::]:*                  LISTEN     
tcp6       0      0 localhost:6013          [::]:*                  LISTEN     
tcp6       0      0 [::]:sunrpc             [::]:*                  LISTEN     
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN     
udp        0      0 localhost.locald:domain 0.0.0.0:*                          
udp        0      0 0.0.0.0:bootps          0.0.0.0:*                          
udp        0      0 0.0.0.0:sunrpc          0.0.0.0:*                          
udp        0      0 0.0.0.0:mdns            0.0.0.0:*                          
udp        0      0 localhost:323           0.0.0.0:*                          
udp        0      0 0.0.0.0:44485           0.0.0.0:*                          
udp        0      0 0.0.0.0:723             0.0.0.0:*                          
udp6       0      0 [::]:sunrpc             [::]:*                             
udp6       0      0 localhost:323           [::]:*                             
udp6       0      0 [::]:723                [::]:*                             
raw6       0      0 [::]:ipv6-icmp          [::]:*                  7          
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  2      [ ACC ]     STREAM     LISTENING     4065041  /tmp/tmux-0/default
unix  2      [ ACC ]     STREAM     LISTENING     12051    /run/lvm/lvmpolld.socket
unix  2      [ ACC ]     STREAM     LISTENING     12054    /run/lvm/lvmetad.socket
unix  2      [ ACC ]     STREAM     LISTENING     32339    /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     32168    @/tmp/.ICE-unix/2802
unix  2      [ ACC ]     SEQPACKET  LISTENING     12319    /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     25504    @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     16676    /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     16681    /run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     16684    /var/run/rpcbind.sock
unix  2      [ ACC ]     STREAM     LISTENING     31021    /run/user/1000/keyring/control
unix  2      [ ACC ]     STREAM     LISTENING     617926   @/tmp/dbus-a1mprKGD
unix  2      [ ACC ]     STREAM     LISTENING     25593    @/tmp/dbus-q0RhMbYK
unix  2      [ ACC ]     STREAM     LISTENING     16713    /var/run/libvirt/virtlogd-sock
unix  2      [ ACC ]     STREAM     LISTENING     16679    @ISCSID_UIP_ABSTRACT_NAMESPACE
unix  2      [ ACC ]     STREAM     LISTENING     16716    /var/run/libvirt/virtlockd-sock
unix  2      [ ACC ]     STREAM     LISTENING     25594    @/tmp/dbus-rSKXqOLk
unix  2      [ ACC ]     STREAM     LISTENING     32341    /run/user/1000/pulse/native
unix  2      [ ACC ]     STREAM     LISTENING     18788    /var/run/lsm/ipc/sim
unix  2      [ ACC ]     STREAM     LISTENING     19573    /var/lib/gssproxy/default.sock
unix  2      [ ACC ]     STREAM     LISTENING     19060    /var/run/lsm/ipc/simc
unix  2      [ ACC ]     STREAM     LISTENING     31965    @/tmp/dbus-oizCRvvoBb
unix  2      [ ACC ]     STREAM     LISTENING     19574    /run/gssproxy.sock
unix  2      [ ACC ]     STREAM     LISTENING     32353    @/tmp/dbus-uRoh6W8u
unix  2      [ ACC ]     STREAM     LISTENING     36882    @parallels-sga-socket
unix  2      [ ACC ]     STREAM     LISTENING     8862     /run/systemd/journal/stdout
unix  2      [ ACC ]     STREAM     LISTENING     25509    /var/run/libvirt/libvirt-sock
unix  2      [ ACC ]     STREAM     LISTENING     19109    /var/run/abrt/abrt.socket
unix  2      [ ACC ]     STREAM     LISTENING     25511    /var/run/libvirt/libvirt-sock-ro
unix  2      [ ACC ]     STREAM     LISTENING     25513    /var/run/libvirt/libvirt-admin-sock
unix  2      [ ACC ]     STREAM     LISTENING     25505    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     16680    @ISCSIADM_ABSTRACT_NAMESPACE
unix  2      [ ACC ]     STREAM     LISTENING     11971    /run/systemd/private
unix  2      [ ACC ]     STREAM     LISTENING     32200    /run/user/1000/keyring/ssh
unix  2      [ ACC ]     STREAM     LISTENING     32202    /run/user/1000/keyring/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     31449    /tmp/ssh-lE21XgrTDtfk/agent.2802
unix  2      [ ACC ]     STREAM     LISTENING     32169    /tmp/.ICE-unix/2802
unix  2      [ ACC ]     STREAM     LISTENING     617925   @/tmp/dbus-E827lpKg
unix  2      [ ACC ]     STREAM     LISTENING     17641    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     31059    @/tmp/dbus-p3MTGAkF
unix  2      [ ACC ]     STREAM     LISTENING     31493    @/tmp/dbus-ye109xuZcT
```

查询指定端口监听情况

```
[root@localhost log (dev)]$ netstat -lp | grep 10400
tcp        0      0 0.0.0.0:10400           0.0.0.0:*               LISTEN      4533/../../game_eng 
```



返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)