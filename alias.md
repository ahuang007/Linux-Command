# Linux alias 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

相反指令  [unalias](https://github.com/ahuang007/Linux-Command/blob/master/unalias.md)

Linux alias 命令用于设置指令的别名。

用户可利用 alias，自定指令的别名。若仅输入 alias，则可列出目前所有的别名设置。alias 的效力仅及于该次登入的操作。若要每次登入是即自动设好别名，可在 .profile 或 .cshrc 中设定指令的别名。

### 语法

```
alias[别名]=[指令名称]
```

**参数说明**：若不加任何参数，则列出目前所有的别名设置。

### 实例

* 给命令设置别名

```
[huanglijun@localhost ~]$ alias lx='ls -l'
[huanglijun@localhost ~]$ lx
总用量 8
drwxr-xr-x  7 huanglijun huanglijun   78 6月  28 09:37 linux
drwxr-xr-x 32 huanglijun huanglijun 4096 7月  29 10:30 protocol
-rwxr--r--  1 huanglijun huanglijun   76 8月  13 14:47 SvnUpdate.bat
drwxrwxr-x  2 huanglijun huanglijun   91 8月  19 10:10 test

# 列出目前所有的别名设置
[huanglijun@localhost ~]$ alias
alias cls='clear && ls'
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l.='ls -d .* --color=auto'
alias ll='ls -l --color=auto'
alias ls='ls --color=auto'
alias lx='ls -l'
alias vi='vim'
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)