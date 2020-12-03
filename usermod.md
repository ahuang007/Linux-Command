# Linux usermod 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux usermod 命令用于修改用户帐号。

usermod 可用来修改用户帐号的各项设定。

### 语法

```
usermod [-LU][-c <备注>][-d <登入目录>][-e <有效期限>][-f <缓冲天数>][-g <群组>][-G <群组>][-l <帐号名称>][-s <shell>][-u <uid>][用户帐号]
```

**参数说明**：

- -c<备注> 　修改用户帐号的备注文字。
- -d登入目录> 　修改用户登入时的目录。
- -e<有效期限> 　修改帐号的有效期限。
- -f<缓冲天数> 　修改在密码过期后多少天即关闭该帐号。
- -g<群组> 　修改用户所属的群组。
- -G<群组> 　修改用户所属的附加群组。
- -l<帐号名称> 　修改用户帐号名称。
- -L 　锁定用户密码，使密码无效。
- -s<shell> 　修改用户登入后所使用的shell。
- -u<uid> 　修改用户ID。
- -U 　解除密码锁定。

### 实例

更改登录目录

```
[root@localhost xmoba]# useradd andy
[root@localhost xmoba]# mkdir /home/dasheng
[root@localhost xmoba]# ll /home/
total 0
drwx------ 2 andy andy 76 Dec  3 10:36 andy
drwxr-xr-x 2 root root  6 Dec  3 10:36 dasheng
[root@localhost xmoba]# usermod -d /home/dasheng/ andy
```

改变用户的uid

```
[root@localhost xmoba]# usermod -u 1024 andy
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)