# Linux ex 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux ex 命令用于在 Ex 模式下启动 vim 文本编辑器。

ex 执行效果如同 vi -E，使用语法及参数可参照 vi 指令，如要从 Ex 模式回到普通模式，则在 vim 中输入":vi"或":visual"指令即可。

### 语法

```
ex [选项][参数]
```

**参数说明：**

- +数字：从文件指定的数字行开始显示

- -b：使用二进制模式编辑文件
- -c 指令：编辑完第一个文件后执行指定的指令
- -d ：编辑多个文件时，显示差异部分
- -m ：不允许修改文件
- -n ：不使用缓存
- -oN：其中 N 为数字
- -r ：列出缓存，并显示恢复信息
- -R ：以只读的方式打开文件
- -s ：不显示任何错误信息
- -V ：显示指令的详细执行过程
- --help ：显示帮助信息
- --version ：显示版本信息

### 实例

在 ex 指令后输入文件名按回车键后，即可进入 ex 编辑模式，如编辑 testfile 文件，使用的命令格式如下：

```
[huanglijun@localhost test]$ ex file1
```

输出的信息如下：

```
"file1" 4L, 28C
Entering Ex mode.  Type "visual" to go to Normal mode.
```

"testfile"表示文件名，5L表示5 行，95 表示字节数

进入 ex 模式。输入"visual"回到正常模式

它的操作与 vim 中是一样的，此时如果在":"后输入"visual"后按回车键，将进入到 vi 指令全屏界面；如果输入"q"，则退出编辑器。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)