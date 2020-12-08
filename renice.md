# Linux renice 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux renice 命令用于重新指定一个或多个进程（Process）的优先序（一个或多个将根据参数而定）。

**注意：**每一个进程（Process）都有一个唯一的（unique）id。

使用权限：所有使用者。

### 语法

```
renice priority [[-p] pid ...] [[-g] pgrp ...] [[-u] user ...]
```

**参数说明**：

- -p pid 重新指定进程的 id 为 pid 的进程的优先序
- -g pgrp 重新指定进程群组(process group)的 id 为 pgrp 的进程 (一个或多个) 的优先序
- -u user 重新指定进程拥有者为 user 的进程的优先序

### 实例

将进程 id 为 4571 及 3762 的进程与进程拥有者为 root 及 root 的优先序号码加 1

```
[root@localhost work]# sudo renice +1 4571 -u root root -p 3762
4571 (process ID) old priority 0, new priority 1
0 (user ID) old priority -20, new priority 1
0 (user ID) old priority 1, new priority 1
3762 (process ID) old priority 1, new priority 1
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)