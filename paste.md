# Linux paste 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux paste 命令用于合并文件的列。

paste 指令会把每个文件以列对列的方式，一列列地加以合并。

### 语法

```
paste [-s][-d <间隔字符>][--help][--version][文件...]
```

**参数**：

- -d<间隔字符>或--delimiters=<间隔字符> 　用指定的间隔字符取代跳格字符。
- -s或--serial 　串列进行而非平行处理。
- --help 　在线帮助。
- --version 　显示帮助信息。
- [文件…] 指定操作的文件路径

### 实例

使用 paste 指令将文件"file1"、"file2"、"file3"进行合并，输入如下命令：

```
paste file1 file2 file3 #合并指定文件的内容 
```

在执行以上命令之前，首先使用"cat"指令对3个文件内容进行查看，显示如下所示：

```
[huanglijun@localhost test]$ cat file1 #查看文件file1
one 1
two 2
three 3

[huanglijun@localhost test]$ cat file2 #查看文件file2
hello 4
world 5

[huanglijun@localhost test]$ cat file3 #查看文件file3
end 6
```

当合并指令"paste file1 file2 file3"执行后，程序界面中将显示合并后的文件内容，如下所示：

```
[huanglijun@localhost test]$ paste file1 file2 file3
one 1	hello 4	end 6
two 2	world 5	
three 3
```

若使用 paste 指令的参数"-s"，则可以将一个文件中的多行数据合并为一行进行显示。例如，将文件"file1"中的3行数据合并为一行数据进行显示，输入如下命令

```
[huanglijun@localhost test]$ paste -s file1 # 合并指定文件的多行数据
one 1	two 2	three 3
```

注意：参数"-s"只是将 file1 文件的内容调整显示方式，并不会改变原文件的内容格式。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)