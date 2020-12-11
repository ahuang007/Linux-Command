# Linux pwunconv 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux pwunconv 命令用于关闭用户的投影密码。

执行 pwunconv 指令可以关闭用户投影密码，它会把密码从 shadow 文件内，重回存到 passwd 文件里。

### 语法

```
pwunconv
```

### 实例

开启投影密码

```
[root@localhost ~]# cat /etc/shadow | grep root
root:$6$OMnyJVs5$Nk9bQar2nbS/ylEk1PKIvdiZxqr13Pd2AIyGuur/kffBxMnmvDuG33uofw8x.UUskidD8BbB8j7Y8I4TcVRee/:18607:0:99999:7:::
```

关闭投影密码

```
[root@localhost ~]# pwunconv 
[root@localhost ~]# cat /etc/shadow | grep root
cat: /etc/shadow: No such file or directory
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)