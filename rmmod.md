# Linux rmmod 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`rmmod = remove module`

Linux rmmod 命令用于删除模块。

执行 rmmod 指令，可删除不需要的模块。Linux 操作系统的核心具有模块化的特性，应此在编译核心时，务须把全部的功能都放如核心。你可以将这些功能编译成一个个单独的模块，待有需要时再分别载入它们。

### 语法

```
rmmod [-as][模块名称...]
```

**参数**：

- -a 　删除所有目前不需要的模块。
- -s 　把信息输出至syslog常驻服务，而非终端机界面。

### 实例

卸载模块

```
[root@server modules ]$ lsmod | grep sg
sg                     29382  0 
[root@server modules ]$ rmmod sg
[root@server modules ]$ lsmod | grep sg
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
[root@server modules ]$ insmod /lib/modules/2.6.32-754.2.1.el6.x86_64/kernel/drivers/scsi/sg.ko
[root@server modules ]$ lsmod | grep sg                                                        
sg                     29382  0 
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)