# Linux modinfo 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

关联指令 [lsmod](https://github.com/ahuang007/Linux-Command/blob/master/lsmod.md)

Linux modinfo 命令用于显示 kernel 模块的信息。

modinfo 会显示 kernel 模块的对象文件，以显示该模块的相关信息。

### 语法

```
modinfo [-adhpV][模块文件]
```

**参数**：

- -a或--author 　显示模块开发人员。
- -d或--description 　显示模块的说明。
- -h或--help 　显示modinfo的参数使用方法。
- -p或--parameters 　显示模块所支持的参数。
- -V或--version 　显示版本信息。

### 实例

显示sg模块的信息。

```
[root@server modules ]$ modinfo sg
filename:       /lib/modules/2.6.32-754.2.1.el6.x86_64/kernel/drivers/scsi/sg.ko
alias:          char-major-21-*
version:        3.5.34
license:        GPL
description:    SCSI generic (sg) driver
author:         Douglas Gilbert
retpoline:      Y
srcversion:     06E4563437ED6D8D3FB049C
depends:        
vermagic:       2.6.32-754.2.1.el6.x86_64 SMP mod_unload modversions 
parm:           scatter_elem_sz:scatter gather element size (default: max(SG_SCATTER_SZ, PAGE_SIZE)) (int)
parm:           def_reserved_size:size of buffer reserved for each fd (int)
parm:           allow_dio:allow direct I/O (default: 0 (disallow)) (int)
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

