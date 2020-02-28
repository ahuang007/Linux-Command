# Linux gunzip 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux gunzip 命令用于解压文件。

gunzip 是个使用广泛的解压缩程序，它用于解开被 [gzip](https://github.com/ahuang007/Linux-Command/blob/master/gzip.md)压缩过的文件，这些压缩文件预设最后的扩展名为".gz"。事实上 **gunzip 就是 [gzip](https://github.com/ahuang007/Linux-Command/blob/master/gzip.md) 的硬连接**，因此不论是压缩或解压缩，都可通过 [gzip](https://github.com/ahuang007/Linux-Command/blob/master/gzip.md)指令单独完成。

### 语法

**参数**：

```
gunzip [-acfhlLnNqrtvV][-s <压缩字尾字符串>][文件...] 或 gunzip [-acfhlLnNqrtvV][-s <压缩字尾字符串>][目录]
```

- -a或--ascii 　使用ASCII文字模式。
- -c或--stdout或--to-stdout 　把解压后的文件输出到标准输出设备。
- -f或-force 　强行解开压缩文件，不理会文件名称或硬连接是否存在以及该文件是否为符号连接。
- -h或--help 　在线帮助。
- -l或--list 　列出压缩文件的相关信息。
- -L或--license 　显示版本与版权信息。
- -n或--no-name 　解压缩时，若压缩文件内含有远来的文件名称及时间戳记，则将其忽略不予处理。
- -N或--name 　解压缩时，若压缩文件内含有原来的文件名称及时间戳记，则将其回存到解开的文件上。
- -q或--quiet 　不显示警告信息。
- -r或--recursive 　递归处理，将指定目录下的所有文件及子目录一并处理。
- -S<压缩字尾字符串>或--suffix<压缩字尾字符串> 　更改压缩字尾字符串。
- -t或--test 　测试压缩文件是否正确无误。
- -v或--verbose 　显示指令执行过程。
- -V或--version 显示版本信息。

### 实例

```
[huanglijun@localhost test1]$ ls
a.c  a.out  b.c  c.c  d.c  testf.txt

# 用 gzip 压缩 gunzip 
[huanglijun@localhost test1]$ gzip *
[huanglijun@localhost test1]$ ls
a.c.gz  a.out.gz  b.c.gz  c.c.gz  d.c.gz  testf.txt.gz
[huanglijun@localhost test1]$ gunzip *
[huanglijun@localhost test1]$ ls
a.c  a.out  b.c  c.c  d.c  testf.txt

# 用 gzip 压缩 gzip解压
[huanglijun@localhost test1]$ gzip *
[huanglijun@localhost test1]$ ls
a.c.gz  a.out.gz  b.c.gz  c.c.gz  d.c.gz  testf.txt.gz
[huanglijun@localhost test1]$ gzip -dv *
a.c.gz:	 38.3% -- replaced with a.c
a.out.gz:	 69.3% -- replaced with a.out
b.c.gz:	 34.0% -- replaced with b.c
c.c.gz:	 41.8% -- replaced with c.c
d.c.gz:	 38.6% -- replaced with d.c
testf.txt.gz:	  2.5% -- replaced with testf.txt
[huanglijun@localhost test1]$ ls
a.c  a.out  b.c  c.c  d.c  testf.txt


```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)