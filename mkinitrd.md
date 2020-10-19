# Linux mkinitrd 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux mkinitrd 命令用于建立要载入 ramdisk 的映像文件。

mkinitrd 可建立映像文件，以供 Linux 开机时载入 ramdisk。

### 语法

```
mkinitrd [-fv][--omit-scsi-modules][--version][--preload=<模块名称>][--with=<模块名称>][映像文件][Kernel 版本]
```

**参数**：

- -f 若指定的映像问家名称与现有文件重复，则覆盖现有的文件。
- -v执行时显示详细的信息。
- --omit-scsi-modules 不要载入SCSI模块。
- --preload=<模块名称> 指定要载入的模块。
- --with=<模块名称> 指定要载入的模块。
- --version 显示版本信息。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)