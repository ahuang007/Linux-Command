# Linux grpunconv 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux grpunconv 命令用于关闭群组的投影密码。

执行 grpunconv 指令可关闭群组投影密码，它会把密码从 gshadow 文件内，回存到 group 文件里。

### 语法

```
grpunconv
```

### 实例

开启投影密码

```
[root@localhost ~]# grpconv
[root@localhost ~]# cat /etc/gshadow | grep root
root:::
```

关闭投影密码

```
[root@localhost ~]# grpunconv 
[root@localhost ~]# cat /etc/gshadow | grep root
cat: /etc/gshadow: No such file or directory
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)