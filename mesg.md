# Linux mesg 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux mesg 命令用于设置终端机的写入权限。

将 mesg 设置 y 时，其他用户可利用 write 指令将信息直接显示在您的屏幕上。

### 语法

```
mesg [ny]
```

**参数**：

- n 不允许其他用户将信息直接显示在你的屏幕上。
- y 允许其他用户将信息直接显示在你的屏幕上。

### 实例

允许其他用户发信息到当前终端。

root 的终端

```
[root@localhost trunk (dev ✗)]$ mesg y //在这个终端设置允许发送消息

[root@localhost trunk (dev ✗)]$ mesg 
is y

```

其他普通用户的终端：

```
[root@localhost log (dev ✗)]$ write root pts/16   
hello

```

root 的终端 终端显示

```
[root@localhost trunk (dev ✗)]$ 
Message from root@localhost.localdomain on pts/14 at 21:05 ...
hello
EOF

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)