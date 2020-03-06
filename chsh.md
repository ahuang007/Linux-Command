# Linux chsh 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux chsh 命令用于更改使用者 shell 设定。

`chsh = change shell`

使用权限：所有使用者。

### 语法

```
chsh [ -s shell ] [ -l ] [ -u ] [ -v ] [ username ]
```

-s, --shell
指定 用户的 登录 shell.

-l, --list-shells
显示 /etc/shells 中的 shell 列表, 然后退出.

-u, --help
显示 使用方法, 然后退出.

-v, --version
显示 版本信息, 然后退出.

### 实例

显示shell列表

```
[huanglijun@localhost test]$ chsh -l
/bin/sh
/bin/bash
/sbin/nologin
/usr/bin/sh
/usr/bin/bash
/usr/sbin/nologin
/bin/tcsh
/bin/csh

上述指令等价于 
[huanglijun@localhost test]$ cat /etc/shells
```

改变当前的shell。当前的shell 设置为//bin/bash，通过chsh命令，改变shell的设置/bin/csh。

```
[huanglijun@localhost test]$ chsh
Changing shell for huanglijun.
New shell [/bin/bash]: /bin/csh
密码：
Shell changed.

```

通过 -s 参数改变当前的shell设置

```
[huanglijun@localhost test]$ chsh -s /bin/bash
Changing shell for huanglijun.
密码：
Shell changed.

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)