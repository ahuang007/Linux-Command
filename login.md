# Linux login 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

使用 login 命令可以运行用户登录系统。如果没有指定参数，登录时提示输入用户名。

Login 是Linux系统工作时面对的第一个进程，login 进程本身并不是在终端上见到的，见到的其实是getty (get TeleTYpe terminal ，早期电脑上的意思是获取纸带终端，现在可以直接理解成打开终端)，它是由init（通过/etc/inittab）在启动login进程时添加而启动的。

完整的启动链是：init -> getty -> login -> passwd -> shell -> applications 

使用login登录，不但打开了一个shell而且还配置了运行时环境（runtime env），这个配置如果在/etc下是系统级别的配置，如果在你的个人home目录下则是个人配置。

/etc/profile - 面向所有的用户和所有的shell

/etc/bash.bashrc - 面向所有用户的bash配置

~/.bashrc - 你个人的bash配置

### 语法

```
　login[选项][用户名]
```

**login命令选项含义**

| 选项 | 含义                                     |
| ---- | ---------------------------------------- |
| -h   | 使用其他服务器来传递远程主机的名称来登录 |
| -p   | 登录不破坏环境                           |
| -f   | 用来跳过第二次登录身份验证               |

### 实例

使用新的身份登录系统

```
# login
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)