# Linux ulimit 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux ulimit命令用于控制shell程序的资源。

ulimit为shell内建指令，可用来控制shell执行程序的资源。

### 语法

```
ulimit [-aHS][-c <core文件上限>][-d <数据节区大小>][-f <文件大小>][-m <内存大小>][-n <文件数目>][-p <缓冲区大小>][-s <堆叠大小>][-t <CPU时间>][-u <程序数目>][-v <虚拟内存大小>]
```

**参数**：

- -a 　显示目前资源限制的设定。
- -c <core文件上限> 　设定core文件的最大值，单位为区块。
- -d <数据节区大小> 　程序数据节区的最大值，单位为KB。
- -f <文件大小> 　shell所能建立的最大文件，单位为区块。
- -H 　设定资源的硬性限制，也就是管理员所设下的限制。
- -m <内存大小> 　指定可使用内存的上限，单位为KB。
- -n <文件数目> 　指定同一时间最多可开启的文件数。
- -p <缓冲区大小> 　指定管道缓冲区的大小，单位512字节。
- -s <堆叠大小> 　指定堆叠的上限，单位为KB。
- -S 　设定资源的弹性限制。
- -t <CPU时间> 　指定CPU使用时间的上限，单位为秒。
- -u <程序数目> 　用户最多可开启的程序数目。
- -v <虚拟内存大小> 　指定可使用的虚拟内存上限，单位为KB。

### 实例

显示系统资源的设置

```
[huanglijun@localhost test1]$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 126816
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024000
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 126816
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

设置core文件大小

```
[huanglijun@localhost test1]$ ulimit -c 9999
[huanglijun@localhost test1]$ ulimit -a
core file size          (blocks, -c) 9999
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 126816
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024000
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 126816
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)