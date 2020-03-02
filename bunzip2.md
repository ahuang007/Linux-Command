# Linux bunzip2 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux bunzip2 命令是 .bz2 文件的解压缩程序。

bunzip2 可解压缩 .bz2 格式的压缩文件。bunzip2 实际上是 [bzip2](https://github.com/ahuang007/Linux-Command/blob/master/bzip2.md) 的符号连接，执行 bunzip2 与 bzip2 -d 的效果相同。

**语法**：bunzip2 [ -fkvsVL ] [ filenames ...  ]

**参数**：

- -f或--force 　解压缩时，若输出的文件与现有文件同名时，预设不会覆盖现有的文件。若要覆盖，请使用此参数。
- -k或--keep 　在解压缩后，预设会删除原来的压缩文件。若要保留压缩文件，请使用此参数。
- -s或--small 　降低程序执行时，内存的使用量。
- -v或--verbose 　解压缩文件时，显示详细的信息。
- -L,--license,-V或--version 　显示版本信息。

### 实例

解压.bz2文件

```
[huanglijun@localhost test1]$ ls
a.c  a.out  b.c  c.c  d.c  testf.txt

[huanglijun@localhost test1]$ bzip2 a.c
[huanglijun@localhost test1]$ ls
a.c.bz2  a.out  b.c  c.c  d.c  testf.txt

[huanglijun@localhost test1]$ bunzip2 -v a.c.bz2 
  a.c.bz2: done
[huanglijun@localhost test1]$ ls
a.c  a.out  b.c  c.c  d.c  testf.txt
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)