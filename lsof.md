# Linux lsof 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

**lsof(list open files)是一个查看进程打开的文件的工具。**

在 linux 系统中，一切皆文件。通过文件不仅仅可以访问常规数据，还可以访问网络连接和硬件。

所以 lsof 命令不仅可以查看进程打开的文件、目录，还可以查看进程监听的端口等 socket 相关的信息

## 常用选项

**-a** 指示其它选项之间为与的关系
**-c** <进程名> 输出指定进程所打开的文件
**-d** <文件描述符> 列出占用该文件号的进程
**+d** <目录> 输出目录及目录下被打开的文件和目录(不递归)
**+D** <目录> 递归输出及目录下被打开的文件和目录
**-i** <条件> 输出符合条件与网络相关的文件
**-n** 不解析主机名
**-p** <进程号> 输出指定 PID 的进程所打开的文件
**-P** 不解析端口号
**-t** 只输出 PID
**-u** 输出指定用户打开的文件
**-U** 输出打开的 UNIX domain socket 文件
**-h** 显示帮助信息
**-v** 显示版本信息

## 基本输出

如果不带任何选项执行 lsof 命令，会输出系统中所有 active 进程打开的所有文件，结果就是我们被输出的信息所淹没，这没有任何的意义。我们先让 lsof 命令输出当前 Bash 进程打开的文件，并截取其中的一部分结果来介绍输出内容中都包含哪些信息：

```
[root@localhost ~]# lsof -P
COMMAND     PID   TID      USER   FD      TYPE             DEVICE  SIZE/OFF       NODE NAME
systemd       1            root  cwd       DIR              253,0       244         64 /
systemd       1            root  rtd       DIR              253,0       244         64 /
systemd       1            root  txt       REG              253,0   1624552   33792061 /usr/lib/systemd/systemd
systemd       1            root  mem       REG              253,0     20064      35476 /usr/lib64/libuuid.so.1.3.0
systemd       1            root  mem       REG              253,0    265600     312319 /usr/lib64/libblkid.so.1.1.0
systemd       1            root  mem       REG              253,0     90248      35465 /usr/lib64/libz.so.1.2.7
systemd       1            root  mem       REG              253,0    157424      35470 /usr/lib64/liblzma.so.5.2.2
systemd       1            root  mem       REG              253,0     23968      35565 /usr/lib64/libcap-ng.so.0.0.0
systemd       1            root  mem       REG              253,0     19896      35574 /usr/lib64/libattr.so.1.1.0
......
```

**COMMAND**：程序的名称
**PID**：进程标识符
**USER**：进程所有者
**FD**：文件描述符，应用程序通过文件描述符识别该文件
```
	cwd 表示当前的工作目录；
	rtd 表示根目录；
	txt 表示程序的可执行文件；
	mem 表示内存映射文件：
```
**TYPE**：文件类型，如 DIR、REG 等
```
	REG 和 DIR 分别表示普通文件和目录。
	CHR 和 BLK 则分别表示字符和块设备，
	unix、fifo 和 IPv4/IPv6 分别表示 UNIX domain 套接字、先进先出(FIFO)队列和 IPv4/IPv6 套接字。
```
**DEVICE**：以逗号分隔设备编号
**SIZE**：文件的大小(bytes)
**NODE**：索引节点(文件在磁盘上的标识)
**NAME**：打开文件的确切名称

### 查看哪些进程打开了某个文件

* 直接指定文件的名称作为 lsof 的参加就可以查看哪些进程打开了这个文件，下面的命令查询打开了 /bin/bash 文件的进程：

  ```
  [root@localhost ~]# lsof /bin/bash
  COMMAND  PID USER  FD   TYPE DEVICE SIZE/OFF      NODE NAME
  bash    1620 root txt    REG  253,0   964600 100664623 /usr/bin/bash
  bash    1669 root txt    REG  253,0   964600 100664623 /usr/bin/bash
  bash    4571 root txt    REG  253,0   964600 100664623 /usr/bin/bash
  ```

* 除了普通文件，也可以是设备等文件

  ```
  [root@localhost ~]# lsof /dev/sda
  ```

### 查看哪些进程打开了某个目录及目录下的文件

* **+d 选项不执行递归查询**，只查找那些打开了指定目录以及指定目录下文件和目录的进程

  ```
  [root@localhost LinuxDebug64]# lsof +d /var/log
  COMMAND    PID USER   FD   TYPE DEVICE SIZE/OFF     NODE NAME
  VGAuthSer  880 root    2w   REG  253,0    16072 33849919 /var/log/vmware-vgauthsvc.log.0
  VGAuthSer  880 root    4w   REG  253,0    16072 33849919 /var/log/vmware-vgauthsvc.log.0
  vmtoolsd   881 root    3w   REG  253,0    18331 34082641 /var/log/vmware-vmsvc.log
  rsyslogd  1152 root    5w   REG  253,0    31416 34241679 /var/log/cron
  rsyslogd  1152 root    6w   REG  253,0   903043 34241689 /var/log/messages
  rsyslogd  1152 root    7w   REG  253,0  2126821 34241690 /var/log/secure
  ```

*  **+D 选项则会对指定的目录进行递归**

  ```
  [root@localhost LinuxDebug64]# lsof +D /var/log
  COMMAND    PID USER   FD   TYPE DEVICE SIZE/OFF      NODE NAME
  auditd     853 root    4w   REG  253,0  2017101 100674351 /var/log/audit/audit.log
  VGAuthSer  880 root    2w   REG  253,0    16072  33849919 /var/log/vmware-vgauthsvc.log.0
  VGAuthSer  880 root    4w   REG  253,0    16072  33849919 /var/log/vmware-vgauthsvc.log.0
  vmtoolsd   881 root    3w   REG  253,0    18331  34082641 /var/log/vmware-vmsvc.log
  rsyslogd  1152 root    5w   REG  253,0    31416  34241679 /var/log/cron
  rsyslogd  1152 root    6w   REG  253,0   903043  34241689 /var/log/messages
  rsyslogd  1152 root    7w   REG  253,0  2126821  34241690 /var/log/secure
  tuned     1153 root    3w   REG  253,0    15000 101379121 /var/log/tuned/tuned.log
  ```

### 查看某个进程打开的所有文件

* 通过 -p 选项并指定进程的 PID 可以输出该进程打开的所有文件。

  ```
  [root@localhost LinuxDebug64]# ps -ef | grep TransferServer 
  root      3176  1620  2 14:53 pts/1    00:00:00 ./TransferServer
  [root@localhost LinuxDebug64]# lsof -p 3176
  COMMAND    PID USER   FD      TYPE DEVICE SIZE/OFF     NODE NAME
  TransferS 3176 root  cwd       DIR  253,0       99 34002539 /root/projects/xmoba/TransferServer/bin/LinuxDebug64
  TransferS 3176 root  rtd       DIR  253,0      244       64 /
  TransferS 3176 root  txt       REG  253,0 29705840 39919900 /root/projects/xmoba/TransferServer/bin/LinuxDebug64/TransferServer
  TransferS 3176 root  mem       REG  253,0    90248    35465 /usr/lib64/libz.so.1.2.7
  TransferS 3176 root  mem       REG  253,0     7584  9131493 /usr/local/lib/libboost_system.so.1.74.0
  TransferS 3176 root  mem       REG  253,0    43712    16231 /usr/lib64/librt-2.17.so
  TransferS 3176 root  mem       REG  253,0  2156272    35352 /usr/lib64/libc-2.17.so
  TransferS 3176 root  mem       REG  253,0   546088 38612981 /usr/local/lib64/libgcc_s.so.1
  TransferS 3176 root  mem       REG  253,0  1136944    16200 /usr/lib64/libm-2.17.so
  TransferS 3176 root  mem       REG  253,0 16646048 38613320 /usr/local/lib64/libstdc++.so.6.0.28
  TransferS 3176 root  mem       REG  253,0  4100368   534340 /usr/local/lib/libprotobuf-lite.so.17.0.0
  TransferS 3176 root  mem       REG  253,0 34382216  8033397 /usr/local/lib/libprotobuf.so.17.0.0
  TransferS 3176 root  mem       REG  253,0    47424  9131548 /usr/local/lib/libboost_random.so.1.74.0
  TransferS 3176 root  mem       REG  253,0   181320  9136264 /usr/local/lib/libboost_thread.so.1.74.0
  TransferS 3176 root  mem       REG  253,0   142144    16225 /usr/lib64/libpthread-2.17.so
  TransferS 3176 root  mem       REG  253,0   163312    35345 /usr/lib64/ld-2.17.so
  TransferS 3176 root    0u      CHR  136,1      0t0        4 /dev/pts/1
  TransferS 3176 root    1u      CHR  136,1      0t0        4 /dev/pts/1
  TransferS 3176 root    2u      CHR  136,1      0t0        4 /dev/pts/1
  TransferS 3176 root    3u  a_inode   0,10        0     7390 [eventfd]
  TransferS 3176 root    4u  a_inode   0,10        0     7390 [eventpoll]
  TransferS 3176 root    5u  a_inode   0,10        0     7390 [timerfd]
  ```

### 查看指定名称的程序打开的文件

* 通过 -c 选项可以匹配进程运行的程序(可执行文件)名称。

  ```
  [root@localhost LinuxDebug64]# lsof -c TransferServer 
  COMMAND    PID USER   FD      TYPE DEVICE SIZE/OFF     NODE NAME
  TransferS 3176 root  cwd       DIR  253,0       99 34002539 /root/projects/xmoba/TransferServer/bin/LinuxDebug64
  TransferS 3176 root  rtd       DIR  253,0      244       64 /
  TransferS 3176 root  txt       REG  253,0 29705840 39919900 /root/projects/xmoba/TransferServer/bin/LinuxDebug64/TransferServer
  TransferS 3176 root  mem       REG  253,0    90248    35465 /usr/lib64/libz.so.1.2.7
  TransferS 3176 root  mem       REG  253,0     7584  9131493 /usr/local/lib/libboost_system.so.1.74.0
  TransferS 3176 root  mem       REG  253,0    43712    16231 /usr/lib64/librt-2.17.so
  TransferS 3176 root  mem       REG  253,0  2156272    35352 /usr/lib64/libc-2.17.so
  TransferS 3176 root  mem       REG  253,0   546088 38612981 /usr/local/lib64/libgcc_s.so.1
  TransferS 3176 root  mem       REG  253,0  1136944    16200 /usr/lib64/libm-2.17.so
  TransferS 3176 root  mem       REG  253,0 16646048 38613320 /usr/local/lib64/libstdc++.so.6.0.28
  TransferS 3176 root  mem       REG  253,0  4100368   534340 /usr/local/lib/libprotobuf-lite.so.17.0.0
  TransferS 3176 root  mem       REG  253,0 34382216  8033397 /usr/local/lib/libprotobuf.so.17.0.0
  TransferS 3176 root  mem       REG  253,0    47424  9131548 /usr/local/lib/libboost_random.so.1.74.0
  TransferS 3176 root  mem       REG  253,0   181320  9136264 /usr/local/lib/libboost_thread.so.1.74.0
  TransferS 3176 root  mem       REG  253,0   142144    16225 /usr/lib64/libpthread-2.17.so
  TransferS 3176 root  mem       REG  253,0   163312    35345 /usr/lib64/ld-2.17.so
  TransferS 3176 root    0u      CHR  136,1      0t0        4 /dev/pts/1
  TransferS 3176 root    1u      CHR  136,1      0t0        4 /dev/pts/1
  TransferS 3176 root    2u      CHR  136,1      0t0        4 /dev/pts/1
  TransferS 3176 root    3u  a_inode   0,10        0     7390 [eventfd]
  TransferS 3176 root    4u  a_inode   0,10        0     7390 [eventpoll]
  TransferS 3176 root    5u  a_inode   0,10        0     7390 [timerfd]
  ```

### 查看被打开的与网络相关的文件

-i 选项用来查看被打开的和网络相关的文件，其参数的格式如下：
`[46][protocol][@hostname|hostaddr][:service|port]`
**46** 表示 IP 协议的版本
**protocol** 表示网络协议的名称，比如 TCP 或 UDP  
**hostname** 或 hostaddr 表示主机地址
**service** 指 /etc/services 中的名称，比如 smtp 或多个服务的列表
**port** 表示端口号，可以指定一个或多个

-i 选项默认会同时输出 IPv4 和 IPv6 打开的文件：

```
[root@localhost LinuxDebug64]# lsof -i
COMMAND     PID      USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
sshd       1154      root    3u  IPv4   13071      0t0  TCP *:ssh (LISTEN)
sshd       1154      root    4u  IPv6   13073      0t0  TCP *:ssh (LISTEN)
master     1237      root   13u  IPv4   13109      0t0  TCP localhost:smtp (LISTEN)
master     1237      root   14u  IPv6   13110      0t0  TCP localhost:smtp (LISTEN)
sshd       1617      root    3u  IPv4 4836110      0t0  TCP localhost.localdomain:ssh->10.24.1.123:53069 (ESTABLISHED)
sshd       1667      root    3u  IPv4 4837198      0t0  TCP localhost.localdomain:ssh->10.24.1.123:53070 (ESTABLISHED)
sshd      14663      root    3u  IPv4 4752323      0t0  TCP localhost.localdomain:ssh->10.24.1.123:50374 (ESTABLISHED)
sshd      14672      root    3u  IPv4 4752340      0t0  TCP localhost.localdomain:ssh->10.24.1.123:50381 (ESTABLISHED)
memcached 27230 memcached   26u  IPv4 1976010      0t0  TCP *:memcache (LISTEN)
memcached 27230 memcached   27u  IPv6 1976011      0t0  TCP *:memcache (LISTEN)
memcached 27230 memcached   28u  IPv4 1976014      0t0  UDP *:memcache 
memcached 27230 memcached   29u  IPv6 1976015      0t0  UDP *:memcache 
```

**只列出 IPv4 或 IPv6 打开的文件**

```
[root@localhost LinuxDebug64]# lsof -i 4
COMMAND     PID      USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
sshd       1154      root    3u  IPv4   13071      0t0  TCP *:ssh (LISTEN)
master     1237      root   13u  IPv4   13109      0t0  TCP localhost:smtp (LISTEN)
sshd       1617      root    3u  IPv4 4836110      0t0  TCP localhost.localdomain:ssh->10.24.1.123:53069 (ESTABLISHED)
sshd       1667      root    3u  IPv4 4837198      0t0  TCP localhost.localdomain:ssh->10.24.1.123:53070 (ESTABLISHED)
sshd      14663      root    3u  IPv4 4752323      0t0  TCP localhost.localdomain:ssh->10.24.1.123:50374 (ESTABLISHED)
sshd      14672      root    3u  IPv4 4752340      0t0  TCP localhost.localdomain:ssh->10.24.1.123:50381 (ESTABLISHED)
memcached 27230 memcached   26u  IPv4 1976010      0t0  TCP *:memcache (LISTEN)
memcached 27230 memcached   28u  IPv4 1976014      0t0  UDP *:memcache 
[root@localhost LinuxDebug64]# lsof -i 6
COMMAND     PID      USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
sshd       1154      root    4u  IPv6   13073      0t0  TCP *:ssh (LISTEN)
master     1237      root   14u  IPv6   13110      0t0  TCP localhost:smtp (LISTEN)
memcached 27230 memcached   27u  IPv6 1976011      0t0  TCP *:memcache (LISTEN)
memcached 27230 memcached   29u  IPv6 1976015      0t0  UDP *:memcache 
```

**列出与 22 号端口相关的文件**

```
[root@localhost LinuxDebug64]# lsof -i:22
COMMAND   PID USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
sshd     1154 root    3u  IPv4   13071      0t0  TCP *:ssh (LISTEN)
sshd     1154 root    4u  IPv6   13073      0t0  TCP *:ssh (LISTEN)
sshd     1617 root    3u  IPv4 4836110      0t0  TCP localhost.localdomain:ssh->10.24.1.123:53069 (ESTABLISHED)
sshd     1667 root    3u  IPv4 4837198      0t0  TCP localhost.localdomain:ssh->10.24.1.123:53070 (ESTABLISHED)
sshd    14663 root    3u  IPv4 4752323      0t0  TCP localhost.localdomain:ssh->10.24.1.123:50374 (ESTABLISHED)
sshd    14672 root    3u  IPv4 4752340      0t0  TCP localhost.localdomain:ssh->10.24.1.123:50381 (ESTABLISHED)
```

**列出指定范围内被打开的 TCP 端口**

```
[root@localhost LinuxDebug64]# lsof -i:1-1024
COMMAND   PID USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
sshd     1154 root    3u  IPv4   13071      0t0  TCP *:ssh (LISTEN)
sshd     1154 root    4u  IPv6   13073      0t0  TCP *:ssh (LISTEN)
master   1237 root   13u  IPv4   13109      0t0  TCP localhost:smtp (LISTEN)
master   1237 root   14u  IPv6   13110      0t0  TCP localhost:smtp (LISTEN)
sshd     1617 root    3u  IPv4 4836110      0t0  TCP localhost.localdomain:ssh->10.24.1.123:53069 (ESTABLISHED)
sshd     1667 root    3u  IPv4 4837198      0t0  TCP localhost.localdomain:ssh->10.24.1.123:53070 (ESTABLISHED)
sshd    14663 root    3u  IPv4 4752323      0t0  TCP localhost.localdomain:ssh->10.24.1.123:50374 (ESTABLISHED)
sshd    14672 root    3u  IPv4 4752340      0t0  TCP localhost.localdomain:ssh->10.24.1.123:50381 (ESTABLISHED)
```

### 查看某个用户打开的所有文件

* **查看某个用户打开的所有文件**

  ```
  [root@localhost LinuxDebug64]# lsof -u root
  COMMAND     PID USER   FD      TYPE             DEVICE  SIZE/OFF       NODE NAME
  systemd       1 root  cwd       DIR              253,0       244         64 /
  systemd       1 root  rtd       DIR              253,0       244         64 /
  systemd       1 root  txt       REG              253,0   1624552   33792061 /usr/lib/systemd/systemd
  systemd       1 root  mem       REG              253,0     20064      35476 /usr/lib64/libuuid.so.1.3.0
  systemd       1 root  mem       REG              253,0    265600     312319 /usr/lib64/libblkid.so.1.1.0
  systemd       1 root  mem       REG              253,0     90248      35465 /usr/lib64/libz.so.1.2.7
  systemd       1 root  mem       REG              253,0    157424      35470 /usr/lib64/liblzma.so.5.2.2
  ```

* **查看用户 打开的网络相关的文件**

  ```
  [root@localhost LinuxDebug64]# lsof -a -i -u root
  COMMAND   PID USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
  sshd     1154 root    3u  IPv4   13071      0t0  TCP *:ssh (LISTEN)
  sshd     1154 root    4u  IPv6   13073      0t0  TCP *:ssh (LISTEN)
  master   1237 root   13u  IPv4   13109      0t0  TCP localhost:smtp (LISTEN)
  master   1237 root   14u  IPv6   13110      0t0  TCP localhost:smtp (LISTEN)
  sshd     1617 root    3u  IPv4 4836110      0t0  TCP localhost.localdomain:ssh->10.24.1.123:53069 (ESTABLISHED)
  sshd     1667 root    3u  IPv4 4837198      0t0  TCP localhost.localdomain:ssh->10.24.1.123:53070 (ESTABLISHED)
  sshd    14663 root    3u  IPv4 4752323      0t0  TCP localhost.localdomain:ssh->10.24.1.123:50374 (ESTABLISHED)
  sshd    14672 root    3u  IPv4 4752340      0t0  TCP localhost.localdomain:ssh->10.24.1.123:50381 (ESTABLISHED)
  ```

* **排除某个用户**

  ```
  [root@localhost LinuxDebug64]# lsof -a -i -u ^root
  COMMAND     PID      USER   FD   TYPE  DEVICE SIZE/OFF NODE NAME
  memcached 27230 memcached   26u  IPv4 1976010      0t0  TCP *:memcache (LISTEN)
  memcached 27230 memcached   27u  IPv6 1976011      0t0  TCP *:memcache (LISTEN)
  memcached 27230 memcached   28u  IPv4 1976014      0t0  UDP *:memcache 
  memcached 27230 memcached   29u  IPv6 1976015      0t0  UDP *:memcache 
  ```

* **杀掉某个用户打开了文件的所有进程**

  ```
  [root@localhost LinuxDebug64]#  kill -9 $(lsof -t -u dev)
  #注意此命令不要轻易尝试
  ```

### 统计系统打开的文件总数

```
[root@localhost LinuxDebug64]# lsof -P -n | wc -l
3644
```

### 帮助

* -h 选项会输出 lsof 命令的帮助信息：

```
[root@localhost LinuxDebug64]# lsof -h
lsof 4.87
 latest revision: ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/
 latest FAQ: ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ
 latest man page: ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/lsof_man
 usage: [-?abhKlnNoOPRtUvVX] [+|-c c] [+|-d s] [+D D] [+|-f[gG]] [+|-e s]
 [-F [f]] [-g [s]] [-i [i]] [+|-L [l]] [+m [m]] [+|-M] [-o [o]] [-p s]
[+|-r [t]] [-s [p:s]] [-S [t]] [-T [t]] [-u s] [+|-w] [-x [fl]] [--] [names]
Defaults in parentheses; comma-separated set (s) items; dash-separated ranges.
  -?|-h list help          -a AND selections (OR)     -b avoid kernel blocks
  -c c  cmd c ^c /c/[bix]  +c w  COMMAND width (9)    +d s  dir s files
  -d s  select by FD set   +D D  dir D tree *SLOW?*   +|-e s  exempt s *RISKY*
  -i select IPv[46] files  -K list tasKs (threads)    -l list UID numbers
  -n no host names         -N select NFS files        -o list file offset
  -O no overhead *RISKY*   -P no port names           -R list paRent PID
  -s list file size        -t terse listing           -T disable TCP/TPI info
  -U select Unix socket    -v list version info       -V verbose search
  +|-w  Warnings (+)       -X skip TCP&UDP* files     -Z Z  context [Z]
  -- end option scan     
  +f|-f  +filesystem or -file names     +|-f[gG] flaGs 
  -F [f] select fields; -F? for help  
  +|-L [l] list (+) suppress (-) link counts < l (0 = all; default = 0)
                                        +m [m] use|create mount supplement
  +|-M   portMap registration (-)       -o o   o 0t offset digits (8)
  -p s   exclude(^)|select PIDs         -S [t] t second stat timeout (15)
  -T qs TCP/TPI Q,St (s) info
  -g [s] exclude(^)|select and print process group IDs
  -i i   select by IPv[46] address: [46][proto][@host|addr][:svc_list|port_list]
  +|-r [t[m<fmt>]] repeat every t seconds (15);  + until no files, - forever.
       An optional suffix to t is m<fmt>; m must separate t from <fmt> and
      <fmt> is an strftime(3) format for the marker line.
  -s p:s  exclude(^)|select protocol (p = TCP|UDP) states by name(s).
  -u s   exclude(^)|select login|UID set s
  -x [fl] cross over +d|+D File systems or symbolic Links
  names  select named files or files on named file systems
Anyone can list all files; /dev warnings disabled; kernel ID check disabled.
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

