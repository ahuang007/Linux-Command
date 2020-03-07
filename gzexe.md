# Linux gzexe 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux gzexe 命令用于压缩执行文件。

gzexe 是用来压缩执行文件的程序。当您去执行被压缩过的执行文件时，该文件会自动解压然后继续执行，和使用一般的执行文件相同。

### 语法

```
gzexe [-d][执行文件...]
```

**参数**：

- -d 　解开压缩文件。

### 实例

压缩可执行文件

```
[huanglijun@localhost test1]$ ls
a.c  b.c  c.c  d.c  hello  testf.txt
[huanglijun@localhost test1]$ gzexe hello 
hello:	 69.2%
[huanglijun@localhost test1]$ ls
a.c  b.c  c.c  d.c  hello  hello~  testf.txt
[huanglijun@localhost test1]$ gzexe -d hello

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)