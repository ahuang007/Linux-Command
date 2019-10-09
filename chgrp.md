# Linux chgrp 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`chgrp = change group`

Linux chgrp 命令用于变更文件或目录的所属群组。

在 UNIX 系统家族里，文件或目录权限的掌控以拥有者及所属群组来管理。您可以使用 chgrp 指令去变更文件与目录的所属群组，设置方式采用群组名称或群组识别码皆可。

### 语法

```
chgrp [-cfhRv][--help][--version][所属群组][文件或目录...] 或 chgrp [-cfhRv][--help][--reference=<参考文件或目录>][--version][文件或目录...]
```

### 参数说明

　　-c或--changes 效果类似"-v"参数，但仅回报更改的部分。

　　-f或--quiet或--silent 　不显示错误信息。

　　-h或--no-dereference 　只对符号连接的文件作修改，而不更动其他任何相关文件。

　　-R或--recursive 　递归处理，将指定目录下的所有文件及子目录一并处理。

　　-v或--verbose 　显示指令执行过程。

　　--help 　在线帮助。

　　--reference=<参考文件或目录> 　把指定文件或目录的所属群组全部设成和参考文件或目录的所属群组相同。

　　--version 　显示版本信息。

### 实例

实例1：改变文件的群组属性：

```
[huanglijun@localhost test]$ ll | grep file2
-rw-rw-r-- 1 huanglijun huanglijun 16 9月  24 10:20 file2

[huanglijun@localhost test]$ sudo chgrp -v root file2

[huanglijun@localhost test]$ ll | grep file2
-rw-rw-r-- 1 huanglijun root       16 9月  24 10:20 file2
```

说明： 将 file2 文件由 huanglijun 群组改为 root 群组

实例2：根据指定文件改变文件的群组属性

```
[huanglijun@localhost test]$ ll | grep -E "file2|file3"  // grep -E 同时匹配多个关键字–或关系 
-rw-rw-r-- 1 huanglijun root       16 9月  24 10:20 file2
-rw-rw-r-- 1 huanglijun huanglijun  6 9月  24 10:21 file3

[huanglijun@localhost test]$ sudo chgrp --reference=file2 file3

[huanglijun@localhost test]$ ll | grep -E "file2|file3"
-rw-rw-r-- 1 huanglijun root       16 9月  24 10:20 file2
-rw-rw-r-- 1 huanglijun root        6 9月  24 10:21 file3
```

说明： 改变文件 file3 的群组属性，使得文件 file3 的群组属性和参考文件 file2 的群组属性相同

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)