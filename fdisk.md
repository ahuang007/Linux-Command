# Linux fdisk 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux fdisk 是一个创建和维护分区表的程序，它兼容 DOS 类型的分区表、BSD 或者 SUN 类型的磁盘列表。

### 语法

```
fdisk [必要参数][选择参数]
```

**必要参数：**

- -l 列出素所有分区表
- -u 与"-l"搭配使用，显示分区数目

**选择参数：**

- -s<分区编号> 指定分区
- -v 版本信息

**菜单操作说明**



- m ：显示菜单和帮助信息
- a ：活动分区标记/引导分区
- d ：删除分区
- l ：显示分区类型
- n ：新建分区
- p ：显示分区信息
- q ：退出不保存
- t ：设置分区号
- v ：进行分区检查
- w ：保存修改
- x ：扩展应用，高级功能

### 实例

显示当前分区情况：

```
[root@server ~ ]$ fdisk -l

Disk /dev/sda: 42.9 GB, 42949672960 bytes
255 heads, 63 sectors/track, 5221 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00056520

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          39      307200   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              39         549     4096000   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3             549        5222    37538816   83  Linux
```

显示SCSI硬盘的每个分区情况

```
[root@server ~ ]$ fdisk -lu

Disk /dev/sda: 42.9 GB, 42949672960 bytes
255 heads, 63 sectors/track, 5221 cylinders, total 83886080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00056520

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      616447      307200   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2          616448     8808447     4096000   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/sda3         8808448    83886079    37538816   83  Linux
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)