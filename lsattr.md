# Linux lsattr 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux lsattr 命令用于显示文件属性。

用 [chattr](https://github.com/ahuang007/Linux-Command/blob/master/chattr.md) 执行改变文件或目录的属性，可执行 lsattr 指令查询其属性。

### 语法

```
lsattr [-adlRvV][文件或目录...]
```

**参数**：

- -a 　显示所有文件和目录，包括以"."为名称开头字符的额外内建，现行目录"."与上层目录".."。
- -d 　显示，目录名称，而非其内容。
- -l 　此参数目前没有任何作用。
- -R 　递归处理，将指定目录下的所有文件及子目录一并处理。
- -v 　显示文件或目录版本。
- -V 　显示版本信息。

### 实例

1、用 chattr 命令防止系统中某个关键文件被修改：

```
[huanglijun@localhost test]$ sudo chattr +i ./boot.txt
[huanglijun@localhost test]$ lsattr
---------------- ./testfile_1
---------------- ./testfile_2
---------------- ./testfile_3
-----i---------- ./boot.txt.bak
[huanglijun@localhost test]$ mv ./boot.txt ./boot.txt.bak
mv: 无法将"./boot.txt" 移动至"./boot.txt.bak": 不允许的操作
```

修改此文件就要把i属性去掉：

```
[huanglijun@localhost test]$ sudo chattr -i ./boot.txt 
[huanglijun@localhost test]$ mv ./boot.txt ./boot.txt.bak
[huanglijun@localhost test]$ ls
boot.txt.bak  testfile_1  testfile_2  testfile_3
```

使用 lsattr 命令来显示文件属性：

```
[huanglijun@localhost test]$ lsattr
---------------- ./testfile_1
---------------- ./testfile_2
---------------- ./testfile_3
---------------- ./boot.txt.bak
```

2、让某个文件只能往里面追加数据，但不能删除，适用于各种日志文件：

```
[huanglijun@localhost test]$ sudo chattr +a ./testfile_1
[huanglijun@localhost test]$ lsattr
-----a---------- ./testfile_1
---------------- ./testfile_2
---------------- ./testfile_3
---------------- ./boot.txt
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)