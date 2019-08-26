# Linux exit 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux exit 命令用于退出目前的 shell。

执行 exit 可使 shell 以指定的状态值退出。若不设置状态值参数，则shell以预设值退出。状态值0代表执行成功，其他值代表执行失败。exit 也可用在 script，离开正在执行的 script，回到 shell。

相似指令 [logout](https://github.com/ahuang007/Linux-Command/blob/master/logout.md)

### 语法

```
exit [状态值]
```

### 实例

退出终端

```
[huanglijun@localhost ~]$ exit
登出
Connection closing...Socket close.

Connection closed by foreign host.

Disconnected from remote host(192.168.1.243(huanglijun)) at 09:45:46.

Type `help' to learn how to use Xshell prompt.
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)