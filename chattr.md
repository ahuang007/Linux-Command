# Linux chattr 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux chattr 命令用于改变文件属性。

这项指令可改变存放在 ext2 文件系统上的文件或目录属性，这些属性共有以下8种模式：

1. a：让文件或目录仅供附加用途。
2. b：不更新文件或目录的最后存取时间。
3. c：将文件或目录压缩后存放。
4. d：将文件或目录排除在倾倒操作之外。
5. i：不得任意更动文件或目录。
6. s：保密性删除文件或目录。
7. S：即时更新文件或目录。
8. u：预防意外删除。

### 语法

```
chattr [-RV][-v<版本编号>][+/-/=<属性>][文件或目录...]
```

### 参数

　　-R 递归处理，将指定目录下的所有文件及子目录一并处理。

　　-v<版本编号> 设置文件或目录版本。

　　-V 显示指令执行过程。

　　+<属性> 开启文件或目录的该项属性。

　　-<属性> 关闭文件或目录的该项属性。

　　=<属性> 指定文件或目录的该项属性。

### 实例

用chattr命令防止系统中某个关键文件被修改：

```
[huanglijun@localhost test]$ lsattr
---------------- ./testfile_1
---------------- ./testfile_2
---------------- ./testfile_3
---------------- ./boot.txt
[huanglijun@localhost test]$ sudo chattr +i ./boot.txt
[huanglijun@localhost test]$ lsattr
---------------- ./testfile_1
---------------- ./testfile_2
---------------- ./testfile_3
----i----------- ./boot.txt
```

让某个文件只能往里面追加数据，但不能删除，适用于各种日志文件：

```
[huanglijun@localhost test]$ sudo chattr +a ./testfile_1
[huanglijun@localhost test]$ lsattr
-----a---------- ./testfile_1
---------------- ./testfile_2
---------------- ./testfile_3
----i----------- ./boot.txt
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)