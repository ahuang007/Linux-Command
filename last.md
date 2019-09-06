# Linux last 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux last 命令用于显示用户最近登录信息。

使用权限：所有使用者。

### 语法

```
last [options]
```

**参数说明**：

- -R 省略 hostname 的栏位
- -num 展示前 num 个
- username 展示 username 的登入讯息
- tty 限制登入讯息包含终端机代号

### 实例

```
[huanglijun@localhost ~]$ last
huanglij pts/0        192.168.10.252   Fri Sep  6 18:31   still logged in
xkxz     pts/4        192.168.10.140   Fri Sep  6 17:42 - 18:31  (00:48)    
app      pts/4        192.168.10.214   Fri Sep  6 17:14 - 17:15  (00:00)    
xiaopao  pts/20       192.168.10.214   Fri Sep  6 16:06 - 16:55  (00:49)    
xiaopao  pts/19       192.168.10.214   Fri Sep  6 16:05 - 16:06  (00:00)
... 省略 ...
wtmp begins Tue Sep  3 09:51:18 2019
```

简略显示，并指定显示的个数

```
[huanglijun@localhost ~]$ ^C
[huanglijun@localhost ~]$ last -n 5 -R
huanglij pts/0        Fri Sep  6 18:31   still logged in   
xkxz     pts/4        Fri Sep  6 17:42 - 18:31  (00:48)    
app      pts/4        Fri Sep  6 17:14 - 17:15  (00:00)    
xiaopao  pts/20       Fri Sep  6 16:06 - 16:55  (00:49)    
xiaopao  pts/19       Fri Sep  6 16:05 - 16:06  (00:00)    

wtmp begins Tue Sep  3 09:51:18 2019
```

显示最后一列显示主机IP地址

```
[huanglijun@localhost ~]$ last -n 5 -a -i
huanglij pts/0        Fri Sep  6 18:31   still logged in    192.168.10.252
xkxz     pts/4        Fri Sep  6 17:42 - 18:31  (00:48)     192.168.10.140
app      pts/4        Fri Sep  6 17:14 - 17:15  (00:00)     192.168.10.214
xiaopao  pts/20       Fri Sep  6 16:06 - 16:55  (00:49)     192.168.10.214
xiaopao  pts/19       Fri Sep  6 16:05 - 16:06  (00:00)     192.168.10.214

wtmp begins Tue Sep  3 09:51:18 2019
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)