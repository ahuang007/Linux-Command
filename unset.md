# Linux unset 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux unset 命令用于删除变量或函数。

unset 为 shell 内建指令，可删除变量或函数。

### 语法

```
unset [-fv][变量或函数名称]
```

**参数**：

- -f 　仅删除函数。
- -v 　仅删除变量。

### 实例

删除环境变量

```
[root@localhost work]# lx="ls -lh" //设定环境变量

[root@localhost work]# $lx //使用环境变量
total 16
-rwxr-xr-x 1 root root 8208 Dec 23 19:58 test
-rw-r--r-- 1 root root  153 Dec 23 19:54 test.c
drwxr-xr-x 3 root root   79 Dec 23 17:36 TestLinux
drwxr-xr-x 6 root root   84 Nov 20 11:38 TransProjectTool

[root@localhost work]# set | grep lx //查看当前的环境变量
lx='ls -l'

[root@localhost work]# unset lx // 删除环境变量

[root@localhost work]# set | grep lx //查看当前的环境变量
_=lx
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)