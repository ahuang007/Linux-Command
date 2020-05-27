# Linux dirs 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux dirs 命令用于显示目录记录。

显示目录堆叠中的记录。

### 语法

```
dirs [+/-n -l]
```

**参数**：

- +n 显示从左边算起第n笔的目录。
- -n 显示从右边算起第n笔的目录。
- -l 显示目录完整的记录。

### 实例

列出"/root/work"里所有内容的详细信息。可用如下命令。

```
dir -l /root/work
```

下面是显示的内容：

```
[root@localhost test ]$ dir -l /root/work 
total 16
drwxr-xr-x.  9 root root 4096 May 25 17:14 fish_game
drwxr-xr-x.  7 root root 4096 Apr 27 11:47 koa_test
drwxr-xr-x. 25 root root 4096 May 27 12:18 SimpleClient
drwxr-xr-x.  2 root root 4096 May 20 12:29 test
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)