# Linux w 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux w命令用于显示目前登入系统的用户信息。

执行这项指令可得知目前登入系统的用户有哪些人，以及他们正在执行的程序。

单独执行 w 指令会显示所有的用户，您也可指定用户名称，仅显示某位用户的相关信息。

### 语法

```
w [-fhlsuV][用户名称]
```

**参数说明**：

- -f 　开启或关闭显示用户从何处登入系统。
- -h 　不显示各栏位的标题信息列。
- -l 　使用详细格式列表，此为预设值。
- -s 　使用简洁格式列表，不显示用户登入时间，终端机阶段作业和程序所耗费的CPU时间。
- -u 　忽略执行程序的名称，以及该程序耗费CPU时间的信息。
- -V 　显示版本信息。

### 实例

显示当前用户

```
[huanglijun@localhost project]$ w
 09:56:28 up 28 days, 19:35, 11 users,  load average: 0.69, 0.96, 1.43
USER     TTY      FROM             LOGIN@   IDLE   JCPU   PCPU WHAT
lindayon pts/0    192.168.11.89    09:19   12:44   0.04s  0.04s -bash
lindayon pts/1    192.168.11.89    09:20   36.00s  0.47s  0.06s sshd: lindayong [priv]
yiguangj pts/2    192.168.11.233   09:21   16:12   0.12s  0.12s -bash
app      pts/3    192.168.11.233   09:21   34:29   0.01s  0.01s -bash
app      pts/4    192.168.11.164   09:37    8:20   3.56s  0.11s -bash
app      pts/5    192.168.10.31    09:37   13:00   3.54s  0.14s -bash
liuzhu   pts/6    192.168.10.31    09:43    8:44   0.04s  0.01s /bin/bash ./release/release.sh deploy 3d
lindayon pts/7    192.168.11.89    09:51    4:28   6.17s  0.06s sshd: lindayong [priv]
huanglij pts/8    192.168.11.72    09:56    4.00s  0.03s  0.01s w
app      pts/9    192.168.11.72    09:56    9.00s  0.02s  0.02s -bash
```

不显示登录位置

```
[huanglijun@localhost project]$ w -f
 09:59:24 up 28 days, 19:38, 11 users,  load average: 1.00, 1.00, 1.36
USER     TTY        LOGIN@   IDLE   JCPU   PCPU WHAT
lindayon pts/0     09:19   15:40   0.04s  0.04s -bash
lindayon pts/1     09:20    2:36   1.06s  0.06s sshd: lindayong [priv]
yiguangj pts/2     09:21   19:08   0.12s  0.12s -bash
app      pts/3     09:21   37:25   0.01s  0.01s -bash
app      pts/4     09:37   11:16   4.68s  0.11s -bash
app      pts/5     09:37   15:56   4.09s  0.14s -bash
liuzhu   pts/6     09:43   11:40   0.04s  0.01s /bin/bash ./release/release.sh deploy 3d
lindayon pts/7     09:51    7:24  10.12s  0.06s sshd: lindayong [priv]
huanglij pts/8     09:56    4.00s  0.02s  0.00s w -f
app      pts/9     09:56    3:05   0.02s  0.02s -bash
```

以精简模式显示

```
[huanglijun@localhost project]$ clear
[huanglijun@localhost project]$ w -s
 09:59:49 up 28 days, 19:39, 11 users,  load average: 0.85, 0.97, 1.34
USER     TTY      FROM              IDLE WHAT
lindayon pts/0    192.168.11.89    16:05  -bash
lindayon pts/1    192.168.11.89     3:01  sshd: lindayong [priv]
yiguangj pts/2    192.168.11.233   19:33  -bash
app      pts/3    192.168.11.233   37:50  -bash
app      pts/4    192.168.11.164   11:41  -bash
app      pts/5    192.168.10.31    16:21  -bash
liuzhu   pts/6    192.168.10.31    12:05  /bin/bash ./release/release.sh deploy 3d
lindayon pts/7    192.168.11.89     7:49  sshd: lindayong [priv]
huanglij pts/8    192.168.11.72     5.00s w -s
app      pts/9    192.168.11.72     3:30  -bash
```

不显示标题

```
[huanglijun@localhost project]$ w -h
lindayon pts/0    192.168.11.89    09:19   16:25   0.04s  0.04s -bash
lindayon pts/1    192.168.11.89    09:20    3:21   1.20s  0.06s sshd: lindayong [priv]
yiguangj pts/2    192.168.11.233   09:21   19:53   0.12s  0.12s -bash
app      pts/3    192.168.11.233   09:21   38:10   0.01s  0.01s -bash
app      pts/4    192.168.11.164   09:37   12:01   4.95s  0.11s -bash
app      pts/5    192.168.10.31    09:37   16:41   4.23s  0.14s -bash
liuzhu   pts/6    192.168.10.31    09:43   12:25   0.04s  0.01s /bin/bash ./release/release.sh deploy 3d
lindayon pts/7    192.168.11.89    09:51    8:09  11.13s  0.06s sshd: lindayong [priv]
huanglij pts/8    192.168.11.72    09:56    1.00s  0.03s  0.01s w -h
app      pts/9    192.168.11.72    09:56    3:50   0.02s  0.02s -bash
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)