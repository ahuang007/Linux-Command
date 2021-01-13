# Linux pkill 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux pkill 用于杀死一个进程，与 [kill](https://github.com/ahuang007/Linux-Command/blob/master/kill.md) 不同的是它会杀死指定名字的所有进程，类似于 [killall](https://github.com/ahuang007/Linux-Command/blob/master/killall.md) 命令。

kill 命令杀死指定进程 PID，需要配合 ps 使用，而 pkill 直接对进程对名字进行操作，更加方便。

### 语法

```
  pkill [选项]  name
```

**参数说明**：

- name ： 进程名

选项包含如下几个参数：

- -o 仅向找到的最小（起始）进程号发送信号 -n 仅向找到的最大（结束）进程号发送信号

- -P 指定父进程号发送信号
- -g 指定进程组
- -t 指定开启进程的终端

### 实例

```
[root@localhost accountserver]# ps -ef | grep skynet | grep -v grep
root      2079     1  4 14:17 ?        00:00:00 ./skynet/skynet ./sh/config.account

[root@localhost accountserver]# pkill -9 skynet //结束所有的 skynet 进程

[root@localhost accountserver]# ps -ef | grep skynet | grep -v grep
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)