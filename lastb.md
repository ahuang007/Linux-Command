# Linux lastb 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux lastb 命令用于列出登入系统失败的用户相关信息。

单独执行 lastb 指令，它会读取位于 /var/log 目录下，名称为 btmp 的文件，并把该文件内容

记录的登入失败的用户名单，全部显示出来。

### 语法

```
lastb [-adRx][-f <记录文件>][-n <显示列数>][帐号名称...][终端机编号...]
```

**参数说明**：

- -a 　把从何处登入系统的主机名称或IP地址显示在最后一行。
- -d 　将IP地址转换成主机名称。
- -f<记录文件> 　指定记录文件。
- -n<显示列数>或-<显示列数> 　设置列出名单的显示列数。
- -R 　不显示登入系统的主机名称或IP地址。
- -x 　显示系统关机，重新开机，以及执行等级的改变等信息。

### 实例

显示登录失败的用户

```
[huanglijun@localhost ~]$ sudo lastb
xiaopaox ssh:notty    192.168.1.243    Wed Sep  4 16:00 - 16:00  (00:00)    
xiaopaox ssh:notty    192.168.1.243    Wed Sep  4 16:00 - 16:00  (00:00)    
xiaopaox ssh:notty    192.168.1.243    Wed Sep  4 15:59 - 15:59  (00:00)    
xiaopaox ssh:notty    192.168.1.243    Wed Sep  4 15:59 - 15:59  (00:00)    
app      ssh:notty    192.168.11.233   Tue Sep  3 11:22 - 11:22  (00:00)    
root     pts/6                         Tue Sep  3 10:18 - 10:18  (00:00)    
app      pts/4                         Tue Sep  3 10:03 - 10:03  (00:00)    

btmp begins Tue Sep  3 10:03:57 2019
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)