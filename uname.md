# Linux uname 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux uname（英文全拼：unix name）命令用于显示系统信息。

uname 可显示电脑以及操作系统的相关信息。

### 语法

```
uname [-amnrsv][--help][--version]
```

**参数说明**：

- -a或--all 　显示全部的信息。
- -m或--machine 　显示电脑类型。
- -n或-nodename 　显示在网络上的主机名称。
- -r或--release 　显示操作系统的发行编号。
- -s或--sysname 　显示操作系统名称。
- -v 　显示操作系统的版本。
- --help 　显示帮助。
- --version 　显示版本信息。

### 实例

显示系统信息：

```
[root@localhost xmoba]# uname -a
Linux localhost.localdomain 3.10.0-1062.el7.x86_64 #1 SMP Wed Aug 7 18:08:02 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

显示计算机类型：

```
[root@localhost xmoba]# uname -m
x86_64
```

显示计算机名：

```
[root@localhost xmoba]# uname -n
localhost.localdomain
```

显示操作系统发行编号：

```
[root@localhost xmoba]# uname -r
3.10.0-1062.el7.x86_64
```

显示操作系统名称：

```
[root@localhost xmoba]# uname -s
Linux
```

显示系统版本与时间：

```
[root@localhost xmoba]# uname -v
#1 SMP Wed Aug 7 18:08:02 UTC 2019
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)