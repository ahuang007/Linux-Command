# Linux wc 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux wc 命令用于计算字数。
`wc= word count`

利用 wc 指令我们可以计算文件的 Byte 数、字数、或是列数，若不指定文件名称、或是所给予的文件名为"-"，则wc 指令会从标准输入设备读取数据。

### 语法

```
wc [-clw][--help][--version][文件...]
```

**参数**：

- -c或--bytes或--chars 只显示Bytes数。
- -l或--lines 只显示行数。
- -w或--words 只显示字数。
- --help 在线帮助。
- --version 显示版本信息。

### 实例

在默认的情况下，wc将计算指定文件的**行数、字数，以及字节数**。使用的命令为：

```
wc testfile 
```

先查看testfile文件的内容，可以看到：

```
[root@localhost test ]$ cat testfile
abc
abc
abc
123
123
123
def
def
def
4
4
qw

```

### 使用 wc 统计，结果如下：

```
[root@localhost test ]$ wc testfile
13 12 44 testfile
```

其中，3 个数字分别表示testfile文件的行数、单词数，以及该文件的字节数。

如果想同时统计多个文件的信息，例如同时统计testfile、testfile_1、testfile_2，可使用如下命令：

```
wc testfile testfile_1 testfile_2
```

输出结果如下：w

```
[root@localhost test ]$ wc testfile testfile1
13 12 44 testfile
 9  9 18 testfile1
22 21 62 total
```

### 使用 wc 统计文件夹下所有文件

```
# 统计当前文件夹下所有lua文件的行数

[root@localhost fish_game (dev ✗)]$ wc -l ` find  .  -name   "*.lua" `
......
1187251 total

# 统计当前文件夹下所有lua文件的单词数

[root@localhost fish_game (dev ✗)]$ wc -w ` find  .  -name   "*.lua" `
......
1800744 total

# 统计当前文件夹下所有lua文件的 行数、单词数，以及文件的字节数
[root@localhost fish_game (dev ✗)]$ wc ` find  .  -name   "*.lua" `
......
 1187251  1800744 40077704 total
```





返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)