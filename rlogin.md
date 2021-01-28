# Linux rlogin 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux rlogin 命令用于远端登入。

执行 rlogin 指令开启终端机阶段操作，并登入远端主机。

### 语法

```
rlogin [-8EL][-e <脱离字符>][-l <用户名称>][主机名称或IP地址]
```

**必要参数**：

- -E 忽略escape字符
- -8 只识别8位字的字符
- -L 允许rlogin会话运行在litout模式
- -ec 设置escape字符为c
- -c 断开连接前要求确认
- -a 强制要求远程主机在发送完一个空的本地用户名之后请求一个密码
- -f 向远端主机发送一个本地认证
- -F 向远程主机发送一个可转寄的本地认证
- -7 强制执行7为的传输
- -d 打开用于远端主机通信的TCP套接口的调试
- -k 要求包含远端主机的tisckets
- -x 启动数据传输的DES加密
- -4 只使用 kerkberos的版本4的认证

**选择参数**：

-e<字符> 设置退出字符

-l<用户> 指定登陆的用户

-t<终端类型> 设置终端类型

### 实例

显示rlogin服务是否开启

```
# chkconfig --list //检测rlogin服务是否开启
```

开启rlogin服务

```
# chkconfig rlogin on //开启rlogin服务
```

登陆远程主机

```
# rlogin 192.168.1.88
Password：
Password：
Login incorrect
Login:root
Passwd:
Login incorrect
Login:kk
Passwd:
```

指定用户名登陆远程主机

```
# rlogin 192.168.1.88 -l hnlinux

Passord:
Last login：Mon May 28 15：30:25 from 192.168.1.88

# 
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)