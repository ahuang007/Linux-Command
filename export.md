# Linux export 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux export 命令用于设置或显示环境变量。

在 shell 中执行程序时，shell 会提供一组环境变量。export 可新增，修改或删除环境变量，供后续执行的程序使用。export 的效力仅限于该次登陆操作。

### 语法

```
export [-fnp][变量名称]=[变量设置值]
```

**参数说明**：

- -f 　代表[变量名称]中为函数名称。
- -n 　删除指定的变量。变量实际上并未删除，只是不会输出到后续指令的执行环境中。
- -p 　列出所有的shell赋予程序的环境变量。

### 实例

列出当前所有的环境变量

```
[root@localhost ~]# export -p //列出当前的环境变量值
declare -x HISTCONTROL="ignoredups"
declare -x HISTSIZE="1000"
declare -x HOME="/root"
declare -x HOSTNAME="localhost.localdomain"
declare -x LANG="en_US.UTF-8"
declare -x LESSOPEN="||/usr/bin/lesspipe.sh %s"
declare -x LOGNAME="root"
declare -x MAIL="/var/spool/mail/root"
declare -x OLDPWD
declare -x PATH="/root/perl5/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin"
declare -x PERL5LIB="/root/perl5/lib/perl5:"
declare -x PERL_LOCAL_LIB_ROOT=":/root/perl5"
declare -x PERL_MB_OPT="--install_base /root/perl5"
declare -x PERL_MM_OPT="INSTALL_BASE=/root/perl5"
declare -x PWD="/root"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_CLIENT="10.24.1.123 53497 22"
declare -x SSH_CONNECTION="10.24.1.123 53497 10.4.1.198 22"
declare -x SSH_TTY="/dev/pts/0"
declare -x TERM="xterm"
declare -x USER="root"
declare -x XDG_RUNTIME_DIR="/run/user/0"
declare -x XDG_SESSION_ID="20000"
```

定义环境变量赋值

```
[root@localhost ~]# export MYENV=7 //定义环境变量并赋值
[root@localhost ~]# export -p
declare -x HISTCONTROL="ignoredups"
declare -x HISTSIZE="1000"
declare -x HOME="/root"
declare -x HOSTNAME="localhost.localdomain"
declare -x LANG="en_US.UTF-8"
declare -x LESSOPEN="||/usr/bin/lesspipe.sh %s"
declare -x LOGNAME="root"
declare -x MAIL="/var/spool/mail/root"
declare -x MYENV="7" //自定义环境变量
declare -x OLDPWD
declare -x PATH="/root/perl5/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/root/bin"
declare -x PERL5LIB="/root/perl5/lib/perl5:"
declare -x PERL_LOCAL_LIB_ROOT=":/root/perl5"
declare -x PERL_MB_OPT="--install_base /root/perl5"
declare -x PERL_MM_OPT="INSTALL_BASE=/root/perl5"
declare -x PWD="/root"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_CLIENT="10.24.1.123 53497 22"
declare -x SSH_CONNECTION="10.24.1.123 53497 10.4.1.198 22"
declare -x SSH_TTY="/dev/pts/0"
declare -x TERM="xterm"
declare -x USER="root"
declare -x XDG_RUNTIME_DIR="/run/user/0"
declare -x XDG_SESSION_ID="20000"
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)