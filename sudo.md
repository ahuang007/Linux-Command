# Linux sudo 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux sudo 命令以系统管理者的身份执行指令，也就是说，经由 sudo 所执行的指令就好像是 root 亲自执行。

使用权限：在 /etc/sudoers 中有出现的使用者。

### 语法

```
sudo -V
sudo -h
sudo -l
sudo -v
sudo -k
sudo -s
sudo -H
sudo [ -b ] [ -p prompt ] [ -u username/#uid] -s
sudo command
```

**参数说明**：

- -V 显示版本编号
- -h 会显示版本编号及指令的使用方式说明
- -l 显示出自己（执行 sudo 的使用者）的权限
- -v 因为 sudo 在第一次执行时或是在 N 分钟内没有执行（N 预设为五）会问密码，这个参数是重新做一次确认，如果超过 N 分钟，也会问密码
- -k 将会强迫使用者在下一次执行 sudo 时问密码（不论有没有超过 N 分钟）
- -b 将要执行的指令放在背景执行
- -p prompt 可以更改问密码的提示语，其中 %u 会代换为使用者的帐号名称， %h 会显示主机名称
- -u username/#uid 不加此参数，代表要以 root 的身份执行指令，而加了此参数，可以以 username 的身份执行指令（#uid 为该 username 的使用者号码）
- -s 执行环境变数中的 SHELL 所指定的 shell ，或是 /etc/passwd 里所指定的 shell
- -H 将环境变数中的 HOME （家目录）指定为要变更身份的使用者家目录（如不加 -u 参数就是系统管理者 root ）
- command 要以系统管理者身份（或以 -u 更改为其他人）执行的指令

### 实例

sudo命令使用

```
[dev@localhost test]# sudo ls
[sudo] password for dev: 
dev is not in the sudoers file. This incident will be reported.
```

指定用户执行命令

```
[dev@localhost test]# sudo -u dev ls -l
```

以root权限执行上一条命令

```
[root@localhost test]# man sudo
[root@localhost test]# sudo !!
sudo man sudo
```

以特定用户身份进行编辑文本devdev

```
[dev@localhost test]# sudo -u de'v vi ~/www/index.html
//以 de'v 用户身份编辑  home 目录下www目录中的 index.html 文件
```

列出目前的权限

```
[root@localhost test]# sudo -l
Matching Defaults entries for root on localhost:
    !visiblepw, always_set_home, match_group_by_gid, always_query_group_plugin, env_reset, env_keep="COLORS DISPLAY HOSTNAME HISTSIZE KDEDIR LS_COLORS", env_keep+="MAIL PS1 PS2 QTDIR USERNAME LANG LC_ADDRESS LC_CTYPE", env_keep+="LC_COLLATE
    LC_IDENTIFICATION LC_MEASUREMENT LC_MESSAGES", env_keep+="LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE", env_keep+="LC_TIME LC_ALL LANGUAGE LINGUAS _XKB_CHARSET XAUTHORITY", secure_path=/sbin\:/bin\:/usr/sbin\:/usr/bin

User root may run the following commands on localhost:
    (ALL) ALL
```

列出 sudo 的版本信息

```
[root@localhost test]# sudo -V
Sudo version 1.8.23
Configure options: --build=x86_64-redhat-linux-gnu --host=x86_64-redhat-linux-gnu --program-prefix= --disable-dependency-tracking --prefix=/usr --exec-prefix=/usr --bindir=/usr/bin --sbindir=/usr/sbin --sysconfdir=/etc --datadir=/usr/share --includedir=/usr/include --libdir=/usr/lib64 --libexecdir=/usr/libexec --localstatedir=/var --sharedstatedir=/var/lib --mandir=/usr/share/man --infodir=/usr/share/info --prefix=/usr --sbindir=/usr/sbin --libdir=/usr/lib64 --docdir=/usr/share/doc/sudo-1.8.23 --with-logging=syslog --with-logfac=authpriv --with-pam --with-pam-login --with-editor=/usr/bin/vi --with-env-editor --enable-gcrypt --with-ignore-dot --with-tty-tickets --with-ldap --with-ldap-conf-file=/etc/sudo-ldap.conf --with-selinux --with-passprompt=[sudo] password for %p:  --with-linux-audit --with-sssd
Sudoers policy plugin version 1.8.23
Sudoers file grammar version 46

Sudoers path: /etc/sudoers
nsswitch path: /etc/nsswitch.conf
ldap.conf path: /etc/sudo-ldap.conf
ldap.secret path: /etc/ldap.secret
Authentication methods: 'pam'
Syslog facility if syslog is being used for logging: authpriv
Syslog priority to use when user authenticates successfully: notice
Syslog priority to use when user authenticates unsuccessfully: alert
Ignore '.' in $PATH
Send mail if the user is not in sudoers
Lecture user the first time they run sudo
Require users to authenticate by default
Root may run sudo
Always set $HOME to the target user's home directory
Allow some information gathering to give useful error messages
Visudo will honor the EDITOR environment variable
Set the LOGNAME and USER environment variables
Length at which to wrap log file lines (0 for no wrap): 80
Authentication timestamp timeout: 18000.0 minutes
Password prompt timeout: 18000.0 minutes
Number of tries to enter a password: 3
Umask to use or 0777 to use user's: 022
Path to mail program: /usr/sbin/sendmail
Flags for mail program: -t
Address to send mail to: root
Subject line for mail messages: *** SECURITY information for %h ***
Incorrect password message: Sorry, try again.
Path to lecture status dir: /var/db/sudo/lectured
Path to authentication timestamp dir: /run/sudo/ts
Default password prompt: [sudo] password for %p: 
Default user to run commands as: root
Value to override user's $PATH with: /sbin:/bin:/usr/sbin:/usr/bin
Path to the editor for use by visudo: /usr/bin/vi
When to require a password for 'list' pseudocommand: any
When to require a password for 'verify' pseudocommand: all
File descriptors >= 3 will be closed before executing a command
Reset the environment to a default set of variables
Environment variables to check for sanity:
	TZ
	TERM
	LINGUAS
	LC_*
	LANGUAGE
	LANG
	COLORTERM
Environment variables to remove:
	*=()*
	RUBYOPT
	RUBYLIB
	PYTHONUSERBASE
	PYTHONINSPECT
	PYTHONPATH
	PYTHONHOME
	TMPPREFIX
	ZDOTDIR
	READNULLCMD
	NULLCMD
	FPATH
	PERL5DB
	PERL5OPT
	PERL5LIB
	PERLLIB
	PERLIO_DEBUG 
	JAVA_TOOL_OPTIONS
	SHELLOPTS
	BASHOPTS
	GLOBIGNORE
	PS4
	BASH_ENV
	ENV
	TERMCAP
	TERMPATH
	TERMINFO_DIRS
	TERMINFO
	_RLD*
	LD_*
	PATH_LOCALE
	NLSPATH
	HOSTALIASES
	RES_OPTIONS
	LOCALDOMAIN
	CDPATH
	IFS
Environment variables to preserve:
	XAUTHORITY
	_XKB_CHARSET
	LINGUAS
	LANGUAGE
	LC_ALL
	LC_TIME
	LC_TELEPHONE
	LC_PAPER
	LC_NUMERIC
	LC_NAME
	LC_MONETARY
	LC_MESSAGES
	LC_MEASUREMENT
	LC_IDENTIFICATION
	LC_COLLATE
	LC_CTYPE
	LC_ADDRESS
	LANG
	USERNAME
	QTDIR
	PS2
	PS1
	MAIL
	LS_COLORS
	KDEDIR
	HISTSIZE
	HOSTNAME
	DISPLAY
	COLORS
Locale to use while parsing sudoers: C
Compress I/O logs using zlib
Directory in which to store input/output logs: /var/log/sudo-io
File in which to store the input/output log: %{seq}
Add an entry to the utmp/utmpx file when allocating a pty
PAM service name to use: sudo
PAM service name to use for login shells: sudo-i
Attempt to establish PAM credentials for the target user
Create a new PAM session for the command to run in
Maximum I/O log sequence number: 0
Enable sudoers netgroup support
Check parent directories for writability when editing files with sudoedit
Query the group plugin for unknown system groups
Allow commands to be run even if sudo cannot write to the audit log
Allow commands to be run even if sudo cannot write to the log file
Resolve groups in sudoers and match on the group ID, not the name
Log entries larger than this value will be split into multiple syslog messages: 960
File mode to use for the I/O log files: 0600
Execute commands by file descriptor instead of by path: digest_only
Type of authentication timestamp record: tty
Ignore case when matching user names
Ignore case when matching group names
Don't pre-resolve all group names

Local IP address and netmask pairs:
	10.4.1.198/255.255.255.0
	fe80::3de2:cc9d:986c:36d8/ffff:ffff:ffff:ffff::

Sudoers I/O plugin version 1.8.23
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)