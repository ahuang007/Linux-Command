# Linux join 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux join 命令用于将两个文件中，指定栏位内容相同的行连接起来。

找出两个文件中，指定栏位内容相同的行，并加以合并，再输出到标准输出设备。

### 语法

```
join [-i][-a<1或2>][-e<字符串>][-o<格式>][-t<字符>][-v<1或2>][-1<栏位>][-2<栏位>][--help][--version][文件1][文件2]
```

**参数**：

- -a<1或2> 除了显示原来的输出内容之外，还显示指令文件中没有相同栏位的行。
- -e<字符串> 若[文件1]与[文件2]中找不到指定的栏位，则在输出中填入选项中的字符串。
- -i或--igore-case 比较栏位内容时，忽略大小写的差异。
- -o<格式> 按照指定的格式来显示结果。
- -t<字符> 使用栏位的分隔字符。
- -v<1或2> 跟-a相同，但是只显示文件中没有相同栏位的行。
- -1<栏位> 连接[文件1]指定的栏位。
- -2<栏位> 连接[文件2]指定的栏位。
- --help 显示帮助。
- --version 显示版本信息。

### 实例

连接两个文件。

为了清楚地了解join命令，首先通过cat命令显示文件testfile_1和 testfile_2 的内容。

然后以默认的方式比较两个文件，将两个文件中指定字段的内容相同的行连接起来，在终端中输入命令：

```
join testfile_1 testfile_2 
```

首先查看testfile_1、testfile_2 中的文件内容：

```
[huanglijun@localhost test]$ cat testfile_1
Hello 95
Linux 85
test 30

[huanglijun@localhost test]$ cat testfile_2
Hello 2005
Linux 2009
test 2006
```

然后使用join命令，将两个文件连接，结果如下：

```
[huanglijun@localhost test]$ join testfile_1 testfile_2
Hello 95 2005
Linux 85 2009
test 30 2006
```

文件1与文件2的位置对输出到标准输出的结果是有影响的。例如将命令中的两个文件互换，即输入如下命令：

```
join testfile_2 testfile_1
```

最终在标准输出的输出结果将发生变化，如下所示：

```
# 将结果输出到文件
[huanglijun@localhost test]$ join testfile_2 testfile_1 > testfile_3
[huanglijun@localhost test]$ cat testfile_3
Hello 2005 95
Linux 2009 85
test 2006 30
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)