# Linux reboot 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux reboot 命令用于用来重新启动计算机。

若系统的 runlevel 为 0 或 6 ，则重新开机，否则以 [shutdown](https://github.com/ahuang007/Linux-Command/blob/master/shutdown.md) 指令（加上 -r 参数）来取代

### 语法

```
reboot [-n] [-w] [-d] [-f] [-i]
```

**参数**：

- -n : 在重开机前不做将记忆体资料写回硬盘的动作
- -w : 并不会真的重开机，只是把记录写到 /var/log/wtmp 档案里
- -d : 不把记录写到 /var/log/wtmp 档案里（-n 这个参数包含了 -d）
- -f : 强迫重开机，不呼叫 shutdown 这个指令
- -i : 在重开机之前先把所有网络相关的装置先停止

### 实例

重新启动 `等价于 shutdown -r now`

```
[root@server ~ ]$ reboot

Broadcast message from root@server
	(/dev/pts/1) at 10:11 ...

The system is going down for reboot NOW!
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)