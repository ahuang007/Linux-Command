# Linux chfn 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux chfn 命令提供使用者更改个人资讯，用于 finger and mail username

使用权限：所有使用者。

`chfn = change finger information`

### 语法

```
[root@localhost ~]# chfn
```

### 实例

改变finger信息

```
[root@localhost ~]# chfn
Changing finger information for root.
Name [root]: root
Office []: xgame
Office Phone []: 123456
Home Phone []: 123456

Finger information changed.
```

改变账号真实姓名

```
[root@localhost ~]# chfn -f root
Changing finger information for root.
Finger information changed.
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)