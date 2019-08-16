# Linux which 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux which 命令用于查找文件。

which 指令会在环境变量 $PATH 设置的目录里查找符合条件的文件。

### 语法

```
which [文件...]
```

**参数**：

- -n<文件名长度> 　指定文件名长度，指定的长度必须大于或等于所有文件中最长的文件名。
- -p<文件名长度> 　与-n参数相同，但此处的<文件名长度>包括了文件的路径。
- -w 　指定输出时栏位的宽度。
- -V 　显示版本信息。

### 实例

使用指令"which"查看指令"bash"的绝对路径，输入如下命令：

```
[root@server ~ ]$ which bash
/bin/bash
[root@server ~ ]$ which lua
/usr/local/bin/lua
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)