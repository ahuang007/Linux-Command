# Linux eject 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux eject 命令用于退出抽取式设备。

若设备已挂入，则 eject 会先将该设备卸除再退出。

### 语法

```
eject [-dfhnqrstv][-a <开关>][-c <光驱编号>][设备]
```

**参数说明**：

- [设备] 设备可以是驱动程序名称，也可以是挂入点。
- -a<开关>或--auto<开关> 控制设备的自动退出功能。
- -c<光驱编号>或--changerslut<光驱编号> 选择光驱柜中的光驱。
- -d或--default 显示预设的设备，而不是实际执行动作。
- -f或--floppy 退出抽取式磁盘。
- -h或--help 显示帮助。
- -n或--noop 显示指定的设备。
- -q或--tape 退出磁带。
- -r或--cdrom 退出光盘。
- -s或--scsi 以SCSI指令来退出设备。
- -t或--trayclose 关闭光盘的托盘。
- -v或--verbose 执行时，显示详细的说明。

### 实例

```
[root@localhost test ]$ eject //不加参数默认弹出
[root@localhost test ]$ eject -r /dev/cdrom //指定设备
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)