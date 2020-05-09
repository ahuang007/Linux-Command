# Linux uniq 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux uniq 命令用于检查及删除文本文件中重复出现的行列，一般与 [sort](https://github.com/ahuang007/Linux-Command/blob/master/sort.md) 命令结合使用。

uniq 可检查文本文件中重复出现的行列。

### 语法

```
uniq [-cdu][-f<栏位>][-s<字符位置>][-w<字符位置>][--help][--version][输入文件][输出文件]
```

**参数**：

- -c或--count 在每列旁边显示该行重复出现的次数。
- -d或--repeated 仅显示重复出现的行列。
- -f<栏位>或--skip-fields=<栏位> 忽略比较指定的栏位。
- -s<字符位置>或--skip-chars=<字符位置> 忽略比较指定的字符。
- -u或--unique 仅显示出一次的行列。
- -w<字符位置>或--check-chars=<字符位置> 指定要比较的字符。
- --help 显示帮助。
- --version 显示版本信息。
- [输入文件] 指定已排序好的文本文件。如果不指定此项，则从标准读取数据；
- [输出文件] 指定输出的文件。如果不指定此选项，则将内容显示到标准输出设备（显示终端）。

### 实例

文件testfile中有相同的行，使用 uniq 命令删除重复的行，可使用如下命令：

```
uniq testfile
```

testfile中的原有内容为：

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

使用uniq 命令删除重复的行后，有如下输出结果：

```
[root@localhost test ]$ uniq testfile 
abc
123
def
4
qw

```

检查文件并删除文件中重复出现的行，并在行首显示该行重复出现的次数。使用如下命令：

```
uniq -c testfile 
```

结果输出如下：

```
[root@localhost test ]$ uniq -c testfile
      3 abc 		# abc出现了三次
      3 123
      3 def
      2 4
      1 qw
      1 
```

当重复的行并不相邻时，uniq 命令是不起作用的，即若文件内容为以下时，uniq 命令不起作用：

```
[root@localhost test ]$ cat testfile1
b
c
a
b
c
a
b
c
a

```

这时我们就可以使用 sort：

```
[root@localhost test ]$ sort testfile1 | uniq
a
b
c
```

统计各行在文件中出现的次数：

```
[root@localhost test ]$ sort testfile1 | uniq -c
      3 a
      3 b
      3 c
```

在文件中找出重复的行：

```
[root@localhost test ]$ sort testfile1 | uniq -d
a
b
c
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)