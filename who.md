# Linux who 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux who 命令用于显示系统中有哪些使用者正在上面，显示的资料包含了使用者 ID、使用的终端机、从哪边连上来的、上线时间、呆滞时间、CPU 使用量、动作等等。

使用权限：所有使用者都可使用。

### 语法

```
who - [husfV] [user]
```

**参数说明**：

- -H 或 --heading：显示各栏位的标题信息列；
- -i 或 -u 或 --idle：显示闲置时间，若该用户在前一分钟之内有进行任何动作，将标示成"."号，如果该用户已超过24小时没有任何动作，则标示出"old"字符串；
- -m：此参数的效果和指定"am i"字符串相同；
- -q 或--count：只显示登入系统的帐号名称和总人数；
- -s：此参数将忽略不予处理，仅负责解决who指令其他版本的兼容性问题；
- -w 或-T或--mesg或--message或--writable：显示用户的信息状态栏；
- --help：在线帮助；
- --version：显示版本信息。

### 实例

显示当前登录系统的用户

```
[root@server StressTest ]$ who //显示当前登录系统的用户
root     tty1         Aug 13 09:46 (:0)
root     pts/0        Aug 13 09:53 (192.168.11.72)
root     pts/1        Aug 13 09:54 (192.168.11.72)
```

显示标题栏

```
[root@server StressTest ]$ who -H
NAME     LINE         TIME         COMMENT
root     tty1         Aug 13 09:46 (:0)
root     pts/0        Aug 13 09:53 (192.168.11.72)
root     pts/1        Aug 13 09:54 (192.168.11.72)
```

显示用户登录来源

```
[root@server StressTest ]$ who -l -H
NAME     LINE         TIME         IDLE          PID COMMENT
LOGIN    tty5         Aug 13 09:46              2894 id=5
LOGIN    tty4         Aug 13 09:46              2892 id=4
LOGIN    tty3         Aug 13 09:46              2890 id=3
LOGIN    tty6         Aug 13 09:46              2896 id=6
LOGIN    tty2         Aug 13 09:46              2888 id=2
```

显示终端属性

```
[root@server StressTest ]$ who -T -H
NAME       LINE         TIME         COMMENT
root     + tty1         Aug 13 09:46 (:0)
root     + pts/0        Aug 13 09:53 (192.168.11.72)
root     + pts/1        Aug 13 09:54 (192.168.11.72)
```

只显示当前用户

```
[root@server StressTest ]$ who -m -H
NAME     LINE         TIME         COMMENT
root     pts/0        Aug 13 09:53 (192.168.11.72)
```

精简模式显示

```
[root@server StressTest ]$ who -q
root root root
# users=3
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)