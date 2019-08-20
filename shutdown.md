# Linux shutdown 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

相似指令 [reboot](https://github.com/ahuang007/Linux-Command/blob/master/reboot.md)

Linux shutdown命令可以用来进行关机程序，并且在关机以前传送讯息给所有使用者正在执行的程序，shutdown 也可以用来重开机。

使用权限：系统管理者。

### 语法

```
shutdown [-t seconds] [-rkhncfF] time [message]
```

**参数说明**：

- -t seconds : 设定在几秒钟之后进行关机程序。
- -k : 并不会真的关机，只是将警告讯息传送给所有使用者。
- -r : 关机后重新开机。
- -h : 关机后停机。
- -n : 不采用正常程序来关机，用强迫的方式杀掉所有执行中的程序后自行关机。
- -c : 取消目前已经进行中的关机动作。
- -f : 关机时，不做 fcsk 动作(检查 Linux 档系统)。
- -F : 关机时，强迫进行 fsck 动作。
- time : 设定关机的时间。
- message : 传送给所有使用者的警告讯息。

### 实例

立即关机

```
[root@server ~ ]$ shutdown -h now

Broadcast message from root@server
	(/dev/pts/0) at 10:16 ...

The system is going down for halt NOW!
```

指定5分钟后关机

```
[root@server ~ ]$ shutdown +2 "System will shutdown after 2 minutes"

Broadcast message from root@server
	(/dev/pts/1) at 10:21 ...

The system is going down for maintenance in 2 minutes!
System will shutdown after 2 minutes 
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)