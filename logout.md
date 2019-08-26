# Linux logout 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux logout命令用于退出系统。

logout 指令让用户退出系统，其功能和 [login](https://github.com/ahuang007/Linux-Command/blob/master/login.md) 指令相互对应。

相似指令 [exit](https://github.com/ahuang007/Linux-Command/blob/master/exit.md)

区别：logout 退出时会执行 ~/.bash_logout（如果有的话），而 exit 只会作退出工作而不执行~/.bash_logout。

### 语法

```
logout
```

### 实例

退出系统：

```
[huanglijun@localhost project]$ su - app
上一次登录：三 8月  7 11:48:29 CST 2019从 192.168.10.85pts/3 上
[app@localhost ~]$ logout
[huanglijun@localhost project]$ 
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

