# Linux modprobe 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux modprobe 命令用于自动处理可载入模块。

modprobe 可载入指定的个别模块，或是载入一组相依的模块。modprobe 会根据 [depmod](https://github.com/ahuang007/Linux-Command/blob/master/depmod.md) 所产生的相依关系，决定要载入哪些模块。若在载入过程中发生错误，在 modprobe 会卸载整组的模块。

### 语法

```
modprobe [-acdlrtvV][--help][模块文件][符号名称 = 符号值]
```

**参数**：

- -a或--all 　载入全部的模块。
- -c或--show-conf 　显示所有模块的设置信息。
- -d或--debug 　使用排错模式。
- -l或--list 　显示可用的模块。
- -r或--remove 　模块闲置不用时，即自动卸载模块。
- -t或--type 　指定模块类型。
- -v或--verbose 　执行时显示详细的信息。
- -V或--version 　显示版本信息。
- -help 　显示帮助。

### 实例

安装软驱模块：

```
[root@server modules ]$ modprobe -v floppy
insmod /lib/modules/2.6.32-754.2.1.el6.x86_64/kernel/drivers/block/floppy.ko 
```

卸载软驱模块：

```
[root@server modules ]$ modprobe -v -r floppy 

rmmod /lib/modules/2.6.32-754.2.1.el6.x86_64/kernel/drivers/block/floppy.ko
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)