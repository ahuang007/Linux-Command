# Linux userdel 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux userdel 命令用于删除用户帐号。

userdel 可删除用户帐号与相关的文件。若不加参数，则仅删除用户帐号，而不删除相关文件。

### 语法

```
userdel [-r][用户帐号]
```

**参数说明**：

- -r 　删除用户登入目录以及目录中所有文件。

### 实例

删除用户账号

```zsh
[root@localhost work]# useradd admin
[root@localhost work]# ll /home/
total 0
drwx------ 2 admin admin 76 Nov 17 19:37 admin
[root@localhost work]# userdel -r admin
[root@localhost work]# ll /home/
total 0
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)