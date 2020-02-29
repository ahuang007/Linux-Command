# Linux bzip2 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux bzip2 命令是 .bz2 文件的压缩程序。

bzip2 采用新的压缩演算法，压缩效果比传统的 LZ77/LZ78 压缩演算法来得好。若没有加上任何参数，bzip2 压缩完文件后会产生 .bz2 的压缩文件，**并删除原始的文件**。

### 语法

```
bzip2 [-cdfhkLstvVz][--repetitive-best][--repetitive-fast][- 压缩等级][要压缩的文件]
```

**参数**：

- -c或--stdout 　将压缩与解压缩的结果送到标准输出。
- -d或--decompress 　执行解压缩。
- -f或--force 　bzip2在压缩或解压缩时，若输出文件与现有文件同名，预设不会覆盖现有文件。若要覆盖，请使用此参数。
- -h或--help 　显示帮助。
- -k或--keep 　bzip2在压缩或解压缩后，会删除原始的文件。若要保留原始文件，请使用此参数。
- -s或--small 　降低程序执行时内存的使用量。
- -t或--test 　测试.bz2压缩文件的完整性。
- -v或--verbose 　压缩或解压缩文件时，显示详细的信息。
- -z或--compress 　强制执行压缩。
- -L,--license,
- -V或--version 　显示版本信息。
- --repetitive-best 　若文件中有重复出现的资料时，可利用此参数提高压缩效果。
- --repetitive-fast 　若文件中有重复出现的资料时，可利用此参数加快执行速度。
- -压缩等级 　压缩时的区块大小。

### 实例

压缩文件

```
[huanglijun@localhost test1]$ ls
a.c  a.out  b.c  c.c  d.c  testf.txt
[huanglijun@localhost test1]$ bzip2 -v a.c
  a.c:      1.311:1,  6.103 bits/byte, 23.71% saved, 329 in, 251 out.
[huanglijun@localhost test1]$ ls
a.c.bz2  a.out  b.c  c.c  d.c  testf.txt
```
测试解压，检查文件完整性

```
[huanglijun@localhost test1]$ bzip2 -t a.c.bz2 
```
解压.bz2文件

```
[huanglijun@localhost test1]$ bzip2 -d a.c.bz2 
[huanglijun@localhost test1]$ ls
a.c  a.out  b.c  c.c  d.c  testf.txt
```



返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)