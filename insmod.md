# Linux insmod 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

相反指令 [rmmod](https://github.com/ahuang007/Linux-Command/blob/master/rmmod.md)

`insmod = install module`

Linux insmod 命令用于载入模块。

Linux 有许多功能是通过模块的方式，在需要时才载入 kernel。如此可使 kernel 较为精简，进而提高效率，以及保有较大的弹性。这类可载入的模块，通常是设备驱动程序。

### 语法

```
insmod [-fkmpsvxX][-o <模块名称>][模块文件][符号名称 = 符号值]
```

**参数说明**：

- -f 　不检查目前 kernel 版本与模块编译时的 kernel 版本是否一致，强制将模块载入。
- -k 　将模块设置为自动卸除。
- -m 　输出模块的载入信息。
- -o<模块名称> 　指定模块的名称，可使用模块文件的文件名。
- -p 　测试模块是否能正确地载入kernel。
- -s 　将所有信息记录在系统记录文件中。
- -v 　执行时显示详细的信息。
- -x 　不要汇出模块的外部符号。
- -X 　汇出模块所有的外部符号，此为预设置。

### 实例

加载模块

```
[root@server modules ]$ insmod /lib/modules/2.6.32-754.2.1.el6.x86_64/kernel/drivers/scsi/sg.ko
[root@server modules ]$ lsmod | grep sg
sg                     29382  0 
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)