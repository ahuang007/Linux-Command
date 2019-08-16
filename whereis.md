# Linux whereis 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux whereis 命令用于查找文件。

该指令会在特定目录中查找符合条件的文件。这些文件应属于原始代码、二进制文件，或是帮助文件。

该指令只能用于查找**二进制文件**、**源代码文件**和**man手册页**，一般文件的定位需使用 [locate](https://github.com/ahuang007/Linux-Command/blob/master/locate.md) 命令。

### 语法

```
whereis [-bfmsu][-B <目录>...][-M <目录>...][-S <目录>...][文件...]
```

**参数**：



-b 　只查找二进制文件。

-B<目录> 　只在设置的目录下查找二进制文件。

-f 　不显示文件名前的路径名称。

-m 　只查找说明文件。

-M<目录> 　只在设置的目录下查找说明文件。

-s 　只查找原始代码文件。

-S<目录> 　只在设置的目录下查找原始代码文件。

-u 　查找不包含指定类型的文件。

### 实例

使用指令"whereis"查看指令"bash"的位置，输入如下命令：

```
[root@server ~ ]$ whereis bash
bash: /bin/bash /usr/share/man/man1/bash.1.gz
```

注意：以上输出信息从左至右分别为查询的**程序名**、**bash路径**、**bash的man 手册页路径**。

如果用户需要单独查询二进制文件或帮助文件，可使用如下命令：

```
[root@server ~ ]$ whereis -b bash
bash: /bin/bash
[root@server ~ ]$ whereis -m bash
bash: /usr/share/man/man1/bash.1.gz
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)