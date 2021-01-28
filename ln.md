# Linux ln 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux ln 命令是一个非常重要命令，它的功能是为某一个文件在另外一个位置建立一个同步的链接。

当我们需要在不同的目录，用到相同的文件时，我们不需要在每一个需要的目录下都放一个必须相同的文件，我们只要在某个固定的目录，放上该文件，然后在 其它的目录下用ln命令链接（link）它就可以，不必重复的占用磁盘空间。

### 语法

```
 ln [参数][源文件或目录][目标文件或目录]
```

其中参数的格式为

[-bdfinsvF] [-S backup-suffix] [-V {numbered,existing,simple}]

[--help] [--version] [--]

**命令功能** : 
Linux 文件系统中，有所谓的链接(link)，我们可以将其视为档案的别名，而链接又可分为两种 : 硬链接(hard link)与软链接(symbolic link)，硬链接的意思是一个档案可以有多个名称，而软链接的方式则是产生一个特殊的档案，该档案的内容是指向另一个档案的位置。硬链接是存在同一个文件系统中，而软链接却可以跨越不同的文件系统。

不论是硬链接或软链接都不会将原本的档案复制一份，只会占用非常少量的磁碟空间。

**软链接**：

- **1.软链接，以路径的形式存在。类似于Windows操作系统中的快捷方式**
- **2.软链接可以 跨文件系统 ，硬链接不可以**
- **3.软链接可以对一个不存在的文件名进行链接**
- **4.软链接可以对目录进行链接**

**硬链接**：

- **1.硬链接，以文件副本的形式存在。但不占用实际空间。**
- **2.不允许给目录创建硬链接**
- **3.硬链接只有在同一个文件系统中才能创建**

#### 命令参数

**必要参数**：

- -b 删除，覆盖以前建立的链接
- -d 允许超级用户制作目录的硬链接
- -f 强制执行
- -i 交互模式，文件存在则提示用户是否覆盖
- -n 把符号链接视为一般目录
- -s 软链接(符号链接)
- -v 显示详细的处理过程

**选择参数**：

- -S "-S<字尾备份字符串> "或 "--suffix=<字尾备份字符串>"
- -V "-V<备份方式>"或"--version-control=<备份方式>"
- --help 显示帮助信息
- --version 显示版本信息

### 实例

给文件创建软链接，为file1文件创建软链接file1.lnk，如果file1丢失，file1.lnk将失效：

```
[huanglijun@localhost test]$ ln -s file1 file1.lnk
[huanglijun@localhost test]$ ll
总用量 12
-rw-rw-r-- 1 huanglijun huanglijun 20 9月  24 10:19 file1
lrwxrwxrwx 1 huanglijun huanglijun  5 9月  25 10:02 file1.lnk -> file1
-rw-rw-r-- 1 huanglijun huanglijun 16 9月  24 10:20 file2
-rw-rw-r-- 1 huanglijun huanglijun  6 9月  24 10:21 file3
```

给文件创建硬链接，为file1创建硬链接file1.bak，file1.bak与file1的各项属性相同

```
[huanglijun@localhost test]$ ln file1 file1.bak
[huanglijun@localhost test]$ ll
总用量 16
-rw-rw-r-- 2 huanglijun huanglijun 20 9月  24 10:19 file1
-rw-rw-r-- 2 huanglijun huanglijun 20 9月  24 10:19 file1.bak
lrwxrwxrwx 1 huanglijun huanglijun  5 9月  25 10:02 file1.lnk -> file1
-rw-rw-r-- 1 huanglijun huanglijun 16 9月  24 10:20 file2
-rw-rw-r-- 1 huanglijun huanglijun  6 9月  24 10:21 file3

# 修改file1 同时 file1.bak也被修改
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)