# Linux bzip2recover 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux bzip2recover 命令用来修复损坏的 .bz2 文件。

[bzip2](https://github.com/ahuang007/Linux-Command/blob/master/bzip2.md) 是以区块的方式来压缩文件，每个区块视为独立的单位。因此，当某一区块损坏时，便可利用bzip2recover，试着将文件中的区块隔开来，以便解压缩正常的区块。通常只适用在压缩文件很大的情况。

### 语法

```
bzip2recover [.bz2 压缩文件]
```

### 实例

修复.bz2文件

```
[huanglijun@localhost test1]$ ls
a.c.bz2  a.out  b.c  c.c  d.c  testf.txt
[huanglijun@localhost test1]$ bzip2recover a.c.bz2 
bzip2recover 1.0.6: extracts blocks from damaged .bz2 files.
bzip2recover: searching for block boundaries ...
   block 1 runs from 80 to 1926
bzip2recover: splitting into blocks
   writing block 1 to `rec00001a.c.bz2' ...
bzip2recover: finished
[huanglijun@localhost test1]$ ls
a.c.bz2  a.out  b.c  c.c  d.c  rec00001a.c.bz2  testf.txt
[huanglijun@localhost test1]$ bunzip2 rec00001a.c.bz2 
[huanglijun@localhost test1]$ ls
a.c.bz2  a.out  b.c  c.c  d.c  rec00001a.c  testf.txt

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)