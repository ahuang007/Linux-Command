# Linux touch 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux touch 命令用于修改文件或者目录的时间属性，包括存取时间和更改时间。若文件不存在，系统会建立一个新的文件。

[ls](https://github.com/ahuang007/Linux-Command/blob/master/ls.md) -l 可以显示档案的时间记录。

### 语法

```
touch [-acfm][-d<日期时间>][-r<参考文件或目录>] [-t<日期时间>][--help][--version][文件或目录…]
```

- **参数说明**：
- a 改变档案的读取时间记录。
- m 改变档案的修改时间记录。
- c 假如目的档案不存在，不会建立新的档案。与 --no-create 的效果一样。
- f 不使用，是为了与其他 unix 系统的相容性而保留。
- r 使用参考档的时间记录，与 --file 的效果一样。
- d 设定时间与日期，可以使用各种不同的格式。
- t 设定档案的时间记录，格式与 date 指令相同。
- --no-create 不会建立新档案。
- --help 列出指令格式。
- --version 列出版本讯息。

### 实例

使用指令"touch"修改文件"testfile"的时间属性为当前系统时间，输入如下命令：

```
[huanglijun@localhost test]$ touch testfile  #修改文件的时间属性 
```

首先，使用ls命令查看testfile文件的属性，如下所示：

```
[huanglijun@localhost test]$ ls -l testfile  #查看文件的时间属性  
-rw-rw-r-- 1 huanglijun huanglijun 0 9月  18 21:17 testfile
```

执行指令"touch"修改文件属性以后，并再次查看该文件的时间属性，如下所示：

```
[huanglijun@localhost test]$ ls -l testfile  #查看文件的时间属性  
-rw-rw-r-- 1 huanglijun huanglijun 0 9月  18 21:17 testfile
[huanglijun@localhost test]$ touch testfile  #修改文件的时间属性 
[huanglijun@localhost test]$ ls -l testfile 
-rw-rw-r-- 1 huanglijun huanglijun 0 9月  18 21:19 testfile
```

使用指令"touch"时，如果指定的文件不存在，则将创建一个新的空白文件。例如，在当前目录下，使用该指令创建一个空白文件"file"，输入如下命令：

```
[huanglijun@localhost test]$ ls -l testfile
ls: 无法访问testfile: 没有那个文件或目录
[huanglijun@localhost test]$ touch testfile #创建一个名为“testfile”的新的空白文件 
[huanglijun@localhost test]$ ls -l testfile
-rw-rw-r-- 1 huanglijun huanglijun 0 9月  18 21:17 testfile

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)