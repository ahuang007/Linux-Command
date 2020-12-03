# Linux vlock 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux vlock 命令用于锁住虚拟终端。

执行 vlock(virtual console lock) 指令可锁住虚拟终端，避免他人使用。

### 语法

```
vlock [-achv]
```

**参数说明**：

- -a或--all 　锁住所有的终端阶段作业，如果您在全屏幕的终端中使用本参数，则会将用键盘
- 切换终端机的功能一并关闭。
- -c或--current 　锁住目前的终端阶段作业，此为预设值。
- -h或--help 　在线帮助。
- -v或--version 　显示版本信息。

### 实例

锁定虚拟终端

```
[root@localhost xmoba]# vlock 
This tty (pts/0) is not a virtual console.


The pts/0 is now locked by root.
Password: 

// 同 windows WIN+L 锁屏
// 输入密码后可以进入
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)