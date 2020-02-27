# Linux gzip 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux gzip 命令用于压缩文件。

gzip 是个使用广泛的压缩程序，文件经它压缩过后，其名称后面会多出".gz"的扩展名。

### 语法

```
gzip [-acdfhlLnNqrtvV][-S &lt;压缩字尾字符串&gt;][-&lt;压缩效率&gt;][--best/fast][文件...] 或 gzip [-acdfhlLnNqrtvV][-S &lt;压缩字尾字符串&gt;][-&lt;压缩效率&gt;][--best/fast][目录]
```

**参数**：

- -a或--ascii 　使用ASCII文字模式。
- -c或--stdout或--to-stdout 　把压缩后的文件输出到标准输出设备，不去更动原始文件。
- -d或--decompress或----uncompress 　解开压缩文件。
- -f或--force 　强行压缩文件。不理会文件名称或硬连接是否存在以及该文件是否为符号连接。
- -h或--help 　在线帮助。
- -l或--list 　列出压缩文件的相关信息。
- -L或--license 　显示版本与版权信息。
- -n或--no-name 　压缩文件时，不保存原来的文件名称及时间戳记。
- -N或--name 　压缩文件时，保存原来的文件名称及时间戳记。
- -q或--quiet 　不显示警告信息。
- -r或--recursive 　递归处理，将指定目录下的所有文件及子目录一并处理。
- -S<压缩字尾字符串>或----suffix<压缩字尾字符串> 　更改压缩字尾字符串。
- -t或--test 　测试压缩文件是否正确无误。
- -v或--verbose 　显示指令执行过程。
- -V或--version 　显示版本信息。
- -<压缩效率> 　压缩效率是一个介于1－9的数值，预设值为"6"，指定愈大的数值，压缩效率就会愈高。
- --best 　此参数的效果和指定"-9"参数相同。
- --fast 　此参数的效果和指定"-1"参数相同。

### 实例

压缩文件

```
[huanglijun@localhost test1]$ ls # 查看当前文件
a.c  a.out  b.c  c.c  d.c  testf.txt
[huanglijun@localhost test1]$ gzip * # 压缩所有文件
[huanglijun@localhost test1]$ ls
a.c.gz  a.out.gz  b.c.gz  c.c.gz  d.c.gz  testf.txt.gz
```

接范例1， 列出详细的信息

```
[huanglijun@localhost test1]$ gzip -dv * #解压文件 并列出详情
a.c.gz:	 38.3% -- replaced with a.c
a.out.gz:	 69.3% -- replaced with a.out
b.c.gz:	 34.0% -- replaced with b.c
c.c.gz:	 41.8% -- replaced with c.c
d.c.gz:	 38.6% -- replaced with d.c
testf.txt.gz:	  2.5% -- replaced with testf.txt
[huanglijun@localhost test1]$ ls
a.c  a.out  b.c  c.c  d.c  testf.txt
```

接范例1，显示压缩文件的信息

```
[huanglijun@localhost test1]$ gzip -l *
         compressed        uncompressed  ratio uncompressed_name
                225                 329  38.3% a.c
               4792               15528  69.3% a.out
                224                 306  34.0% b.c
                206                 316  41.8% c.c
                218                 319  38.6% d.c
                 67                  40   2.5% testf.txt
               5732               16838  66.1% (totals)
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)