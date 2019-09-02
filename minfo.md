# Linux minfo 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux minfo 命令用于显示 MS-DOS 文件系统的各项参数。

minfo 为 [mtools](https://github.com/ahuang007/Linux-Command/blob/master/mtools.md) 工具指令，可显示 MS-DOS 系统磁盘的各项参数，包括磁区数，磁头数...等。

### 语法

```
minfo [-v][驱动器代号]
```

**参数说明**：

- -v 　除了一般信息外，并显示可开机磁区的内容。

### 实例

显示DOS系统参数

```
# minfo -v C: //显示系统参数
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)