# Linux passwd 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux passwd 命令用来更改使用者的密码

### 语法

```
passwd [-k] [-l] [-u [-f]] [-d] [-S] [username]
```

**必要参数**：

- -d 删除密码
- -f 强迫用户下次登录时必须修改口令
- -w 口令要到期提前警告的天数
- -k 更新只能发送在过期之后
- -l 停止账号使用
- -S 显示密码信息
- -u 启用已被停止的账户
- -x 指定口令最长存活期
- -g 修改群组密码
- 指定口令最短存活期
- -i 口令过期后多少天停用账户

**选择参数**：

- --help 显示帮助信息
- --version 显示版本信息

### 实例

修改用户密码

```
# passwd dasheng  //设置dasheng用户的密码
Changing password for user dasheng.
New password:  //输入新密码，输入的密码无回显
Retype new password:  //确认密码
passwd: password updated successfully
```

显示账号密码信息

```
[root@localhost ~]# passwd -S dasheng
dasheng PS (Password set, SHA512 crypt.)
```

删除用户密码

```
[root@localhost ~]# passwd -d dasheng
Removing password for user dasheng.
passwd: Success
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)