# Linux mshowfat 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux mshowfat 命令用于显示 MS-DOS 文件在 FAT 中的记录。

mshowfat 为 [mtools](https://github.com/ahuang007/Linux-Command/blob/master/mtools.md) 工具指令，可显示 MS-DOS 文件在 FAT 中的记录编号。

### 语法

```
mshowfat [文件...]
```

**参数说明：**

[文件…]： 执行操作的文件相对路径或者绝对路径

### 实例

使用指令 mshowfat 查看文件"autorun.bat"的 FAT 信息，输入如下命令：

```
$ mshowfat autorun.bat 
```

以上命令执行后，文件"autorun.bat"的FAT相关信息将会被显示出来。

注意：执行操作的文件必须是 DOS 文件系统下的文件。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)