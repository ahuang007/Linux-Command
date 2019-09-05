# Linux cmp 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux cmp 命令用于比较两个文件是否有差异。

当相互比较的两个文件完全一样时，则该指令不会显示任何信息。若发现有所差异，预设会标示出第一个不同之处的字符和列数编号。若不指定任何文件名称或是所给予的文件名为"-"，则 cmp 指令会从标准输入设备读取数据。

### 语法

```
cmp [-clsv][-i <字符数目>][--help][第一个文件][第二个文件]
```

**参数**：

- -c或--print-chars 　除了标明差异处的十进制字码之外，一并显示该字符所对应字符。
- -i<字符数目>或--ignore-initial=<字符数目> 　指定一个数目。
- -l或--verbose 　标示出所有不一样的地方。
- -s或--quiet或--silent 　不显示错误信息。
- -v或--version 　显示版本信息。
- --help 　在线帮助。

### 实例

要确定两个文件是否相同，请输入：

```
[huanglijun@localhost test]$ cmp testfile_1 testfile_1_bak 
[huanglijun@localhost test]$ cmp testfile_1 testfile_3
testfile_1 testfile_3 不同：第 7 字节，第 1 行
[huanglijun@localhost test]$ cmp testfile_1 testfile_2_bak 
cmp：testfile_1 已结束
```

如果文件相同，则不显示消息。

如果文件不同，则显示第一个不同的位置；

如果显示消息 cmp: *** 已结束，则两个文件 的第一部分 相同，但在 未结束的文件中还有其他数据。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)