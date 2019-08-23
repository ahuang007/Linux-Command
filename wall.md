# Linux wall 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux wall 命令会将讯息传给每一个 mesg 设定为 yes 的上线使用者。当使用终端机介面做为标准传入时, 讯息结束时需加上 EOF (通常用 Ctrl+D)。

使用权限：所有使用者。

### 语法

```
wall [ message ]
```

### 实例

传讯息"hi" 给每一个使用者

```
[huanglijun@localhost project]$ wall
hi

Broadcast message from huanglijun@localhost.localdomain (pts/6) (Fri Aug 23 10:26:47 2019):

hi

```

广播消息

```
[app@localhost service]$ 
Broadcast message from huanglijun@localhost.localdomain (pts/6) (Fri Aug 23 10:26:47 2019):

hi
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)