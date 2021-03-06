# Linux fmt 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux fmt 命令用于编排文本文件。

fmt 指令会从指定的文件里读取内容，将其依照指定格式重新编排后，输出到标准输出设备。若指定的文件名为"-"，则fmt指令会从标准输入设备读取数据。

### 语法

```
fmt [-cstu][-p<列起始字符串>][-w<每列字符数>][--help][--version][文件...]
```

**参数说明**：

- -c或--crown-margin 每段前两列缩排。
- -p<列起始字符串>或-prefix=<列起始字符串> 仅合并含有指定字符串的列，通常运用在程序语言的注解方面。
- -s或--split-only 只拆开字数超出每列字符数的列，但不合并字数不足每列字符数的列。
- -t或--tagged-paragraph 每列前两列缩排，但第1列和第2列的缩排格式不同。
- -u或--uniform-spacing 每个字符之间都以一个空格字符间隔，每个句子之间则两个空格字符分隔。
- -w<每列字符数>或--width=<每列字符数>或-<每列字符数> 设置每列的最大字符数。
- --help 在线帮助。
- --version 显示版本信息。

### 实例

重排指定文件。如文件 a.txt 文字，可以通过命令对该文件格式进行重排，其命令为：

```
[huanglijun@localhost test]$ cat a.txt 
1
2
3
4
5
a
b
c
dd df dfdf asdfadfadfa
e
xfadfadf
y
z
[huanglijun@localhost test]$ fmt a.txt 
1 2 3 4 5 a b c dd df dfdf asdfadfadfa e xfadfadf y z

```

将文件 a.txt 重新排成 10 个字符一行，并在标准输出设备上输出，其命令应该为：

```
[huanglijun@localhost test]$ fmt -w 10 a.txt 
1 2 3 4 5
a b c dd
df dfdf
asdfadfadfa
e
xfadfadf
y z

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)