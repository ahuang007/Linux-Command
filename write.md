# Linux write 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux write 命令用于传讯息给其他使用者。

使用权限：所有使用者。

### 语法

```
write user [ttyname]
```

**参数说明**：

- user : 预备传讯息的使用者帐号
- ttyname : 如果使用者同时有两个以上的 tty 连线，可以自行选择合适的 tty 传讯息

### 实例

传讯息给 app，此时 app 只有一个连线

```
[qtds@localhost project]$ write app
write: app is logged in more than once; writing to pts/0
123456
```

接下来就是将讯息打上去，结束请按 ctrl+c

传讯息给 app，app的连线有 pts/2，pts/3

```
[qtds@localhost project]$ write app pts/2
```

接下来就是将讯息打上去，结束请按 ctrl+c

**注意：**若对方设定 mesg n，则此时讯席将无法传给对方。

接收方显示如下：

```
[app@localhost project]$

Message from qtds@localhost.localdomain on pts/7 at 11:52 ...
123456
EOF
```



返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)