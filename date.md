# Linux date 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux date 命令可以用来显示或设定系统的日期与时间，在显示方面，使用者可以设定欲显示的格式，格式设定为一个加号后接数个标记，其中可用的标记列表如下：

时间方面：

- % : 印出 %
- %n : 下一行
- %t : 跳格
- %H : 小时(00..23)
- %I : 小时(01..12)
- %k : 小时(0..23)
- %l : 小时(1..12)
- %M : 分钟(00..59)
- %p : 显示本地 AM 或 PM
- %r : 直接显示时间 (12 小时制，格式为 hh:mm:ss [AP]M)
- %s : 从 1970 年 1 月 1 日 00:00:00 UTC 到目前为止的秒数
- %S : 秒(00..61)
- %T : 直接显示时间 (24 小时制)
- %X : 相当于 %H:%M:%S
- %Z : 显示时区

日期方面：

- %a : 星期几 (Sun..Sat)
- %A : 星期几 (Sunday..Saturday)
- %b : 月份 (Jan..Dec)
- %B : 月份 (January..December)
- %c : 直接显示日期与时间
- %d : 日 (01..31)
- %D : 直接显示日期 (mm/dd/yy)
- %h : 同 %b
- %j : 一年中的第几天 (001..366)
- %m : 月份 (01..12)
- %U : 一年中的第几周 (00..53) (以 Sunday 为一周的第一天的情形)
- %w : 一周中的第几天 (0..6)
- %W : 一年中的第几周 (00..53) (以 Monday 为一周的第一天的情形)
- %x : 直接显示日期 (mm/dd/yy)
- %y : 年份的最后两位数字 (00.99)
- %Y : 完整年份 (0000..9999)

若是不以加号作为开头，则表示要设定时间，而时间格式为 MMDDhhmm\[\[CC\]YY]\[.ss\]，其中 MM 为月份，DD 为日，hh 为小时，mm 为分钟，CC 为年份前两位数字，YY 为年份后两位数字，ss 为秒数。

使用权限：所有使用者。

当您不希望出现无意义的 0 时(比如说 1999/03/07)，则可以在标记中插入 - 符号，比如说 date '+%-H:%-M:%-S' 会把时分秒中无意义的 0 给去掉，像是原本的 08:09:04 会变为 8:9:4。另外，只有取得权限者(比如说 root)才能设定系统时间。

当您以 root 身分更改了系统时间之后，请记得以 clock -w 来将系统时间写入 CMOS 中，这样下次重新开机时系统时间才会持续抱持最新的正确值。

### 语法

```
date [-u] [-d datestr] [-s datestr] [--utc] [--universal] [--date=datestr] [--set=datestr] [--help] [--version] [+FORMAT] [MMDDhhmm[[CC]YY][.ss]]
```

**参数说明**：

- -d datestr : 显示 datestr 中所设定的时间 (非系统时间)
- --help : 显示辅助讯息
- -s datestr : 将系统时间设为 datestr 中所设定的时间
- -u : 显示目前的格林威治时间
- --version : 显示版本编号

### 实例

显示当前时间

```
[huanglijun@localhost ~]$ date
2019年 08月 15日 星期四 11:31:09 CST
[huanglijun@localhost ~]$ date '+%c'
2019年08月15日 星期四 11时31分17秒
[huanglijun@localhost ~]$ date '+%D'
08/15/19
[huanglijun@localhost ~]$ date '+%x'
2019年08月15日
[huanglijun@localhost ~]$ date '+%T'
11:31:26
[huanglijun@localhost ~]$ date '+%X'
11时31分29秒
```

按自己的格式输出

```
[huanglijun@localhost ~]$ date '+time : $%H:%M %P -hello'
time : $11:33 上午 -hello
```

显示时间后跳行，再显示目前日期

```
[huanglijun@localhost ~]$ date '+%T%n%D'
11:46:51
08/15/19
```

显示月份与日数

```
[huanglijun@localhost ~]$ date '+%B %d'
八月 15
```

显示日期与设定时间

```
[root@server ~ ]$ date
Thu Aug 15 11:48:00 CST 2019
[root@server ~ ]$ date -s "11:48:30"
Thu Aug 15 11:48:30 CST 2019
[root@server ~ ]$ date
Thu Aug 15 11:48:30 CST 2019
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)