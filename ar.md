# Linux ar 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`ar = archiver`

Linux ar 命令用于建立或修改备存文件，或是从备存文件中抽取文件。

ar 可让您集合许多文件，成为单一的备存文件。在备存文件中，所有成员文件皆保有原来的属性与权限。

### 语法

```
ar[-dmpqrtx][cfosSuvV][a<成员文件>][b<成员文件>][i<成员文件>][备存文件][成员文件]
```

**参数**：

**必要参数**：

- -d 　删除备存文件中的成员文件。
- -m 　变更成员文件在备存文件中的次序。
- -p 　显示备存文件中的成员文件内容。
- -q 　将文件附加在备存文件末端。
- -r 　将文件插入备存文件中。
- -t 　显示备存文件中所包含的文件。
- -x 　自备存文件中取出成员文件。

**选项参数**：

- a<成员文件> 　将文件插入备存文件中指定的成员文件之后。
- b<成员文件> 　将文件插入备存文件中指定的成员文件之前。
- c 　建立备存文件。
- f 　为避免过长的文件名不兼容于其他系统的ar指令指令，因此可利用此参数，截掉要放入备存文件中过长的成员文件名称。
- i<成员文件> 　将文件插入备存文件中指定的成员文件之前。
- o 　保留备存文件中文件的日期。
- s 　若备存文件中包含了对象模式，可利用此参数建立备存文件的符号表。
- S 　不产生符号表。
- u 　只将日期较新文件插入备存文件中。
- v 　程序执行时显示详细的信息。
- V 　显示版本信息。

### 实例

打包文件

```
[root@localhost work]# ls   //显示当前目录文件   
test  test.c  TestLinux  TransProjectToo

[root@localhost work]#  ar rv test.bak test.c test //打包 test.c test 文件 
ar: creating test.bak
a - test.c
a - test
[root@localhost work]# ls
test  test.bak  test.c  TestLinux  TransProjectTool
```

打包多个文件

```
[root@localhost work]# ar rv test.all test*  //打包以test开头的文件  
ar: creating test.all
a - test
a - test.bak
a - test.c
[root@localhost work]# ls
test  test.all  test.bak  test.c  TestLinux  TransProjectTool
```

显示打包文件的内容

```
[root@localhost work]# ar t test.all 
test
test.bak
test.c
```

删除打包文件的成员文件

```
[root@localhost work]# ar d test.all test.bak
[root@localhost work]# ar t test.all
test
test.c
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)