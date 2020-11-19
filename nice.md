# Linux nice 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux nice 命令以更改过的优先序来执行程序，如果未指定程序，则会印出目前的排程优先序，内定的 adjustment 为 10，范围为 -20（最高优先序）到 19（最低优先序）。

使用权限：所有使用者。

### 语法

```
nice [-n adjustment] [-adjustment] [--adjustment=adjustment] [--help] [--version] [command [arg...]]
```

**参数说明**：

- -n adjustment, -adjustment, --adjustment=adjustment 皆为将该原有优先序的增加 adjustment
- --help 显示求助讯息
- --version 显示版本资讯

### 实例

设置程序运行时的优先级

```
[root@localhost ~]# vi & //后台运行
[1] 22067
[root@localhost ~]# nice vi & //设置默认优先级
[2] 15298

[1]+ Stopped         vi
[root@localhost ~]# nice -n 19 vi & //设置优先级为19
[3] 22132

[2]+  Stopped                 nice vi
[root@localhost ~]# nice -n -20 vi & //设置优先级为 -20
[root@localhost ~]# nice -n -20 vi &
[4] 22159

[3]+  Stopped                 nice -n 19 vi
# ps -l //显示进程
[root@localhost ~]# ps -l
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
0 T     0 22067 30053  0  80   0 - 31087 do_sig pts/1    00:00:00 vi
0 T     0 22073 30053  0  90  10 - 31087 do_sig pts/1    00:00:00 vi
0 T     0 22132 30053  0  99  19 - 31087 do_sig pts/1    00:00:00 vi
4 T     0 22159 30053  0  60 -20 - 31087 do_sig pts/1    00:00:00 vi
0 R     0 22447 30053  0  80   0 - 38338 -      pts/1    00:00:00 ps
4 S     0 30053 30051  0  80   0 - 28920 do_wai pts/1    00:00:01 bash

[4]+  Stopped                 nice -n -20 vi
```

将 ls 的优先序加 1 并执行

```
[root@localhost ~]# nice -n 1 ls
anaconda-ks.cfg  work
```

将 ls 的优先序加 10 并执行

```
[root@localhost ~]# nice ls
anaconda-ks.cfg  work
```

**注意：**优先序 (priority) 为操作系统用来决定 CPU 分配的参数，Linux 使用『回合制(round-robin)』的演算法来做 CPU 排程，优先序越高，所可能获得的 CPU时间就越多。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)