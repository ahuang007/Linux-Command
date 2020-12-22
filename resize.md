# Linux resize命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux resize 命令设置终端机视窗的大小。

执行 resize 指令可设置虚拟终端机的视窗大小。

### 语法

```
resize [-cu][-s <列数> <行数>]
```

**参数**：

- -c 　就算用户环境并非C Shell，也用C Shell指令改变视窗大小。
- -s <列数> <行数> 　设置终端机视窗的垂直高度和水平宽度。
- -u 　就算用户环境并非Bourne Shell，也用Bourne Shell指令改变视窗大小。

### 实例

使用 C shell

```
[root@localhost ~]# resize -c
set noglob;
setenv COLUMNS '245';
setenv LINES '56';
unset noglob;
```

使用 Bourne shell

```
[root@localhost ~]# resize -u
COLUMNS=245;
LINES=56;
export COLUMNS LINES;
```

设置指定大小

```
[root@localhost ~]# resize -s 80 160
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)