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
[huanglijun@localhost project]$ sudo fdisk -l
WARNING: fdisk GPT support is currently new, and therefore in an experimental phase. Use at your own discretion.

磁盘 /dev/nvme0n1：250.1 GB, 250059350016 字节，488397168 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节
磁盘标签类型：gpt


#         Start          End    Size  Type            Name
 1         2048    488396799  232.9G  Linux LVM       
WARNING: fdisk GPT support is currently new, and therefore in an experimental phase. Use at your own discretion.

磁盘 /dev/sda：2000.4 GB, 2000398934016 字节，3907029168 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 4096 字节
I/O 大小(最小/最佳)：4096 字节 / 4096 字节
磁盘标签类型：gpt


#         Start          End    Size  Type            Name
 1         2048       411647    200M  EFI System      EFI System Partition
 2       411648      2508799      1G  Microsoft basic 
 3      2508800   3907028991    1.8T  Linux LVM       

磁盘 /dev/mapper/cl-root：53.7 GB, 53687091200 字节，104857600 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


磁盘 /dev/mapper/cl-swap：16.8 GB, 16844324864 字节，32899072 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


磁盘 /dev/mapper/cl-home：2178.6 GB, 2178630549504 字节，4255137792 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 4096 字节
I/O 大小(最小/最佳)：4096 字节 / 4096 字节

```

显示SCSI硬盘的每个分区情况

```
WARNING: fdisk GPT support is currently new, and therefore in an experimental phase. Use at your own discretion.

磁盘 /dev/nvme0n1：250.1 GB, 250059350016 字节，488397168 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节
磁盘标签类型：gpt


#         Start          End    Size  Type            Name
 1         2048    488396799  232.9G  Linux LVM       
WARNING: fdisk GPT support is currently new, and therefore in an experimental phase. Use at your own discretion.

磁盘 /dev/sda：2000.4 GB, 2000398934016 字节，3907029168 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 4096 字节
I/O 大小(最小/最佳)：4096 字节 / 4096 字节
磁盘标签类型：gpt


#         Start          End    Size  Type            Name
 1         2048       411647    200M  EFI System      EFI System Partition
 2       411648      2508799      1G  Microsoft basic 
 3      2508800   3907028991    1.8T  Linux LVM       

磁盘 /dev/mapper/cl-root：53.7 GB, 53687091200 字节，104857600 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


磁盘 /dev/mapper/cl-swap：16.8 GB, 16844324864 字节，32899072 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


磁盘 /dev/mapper/cl-home：2178.6 GB, 2178630549504 字节，4255137792 个扇区
Units = 扇区 of 1 * 512 = 512 bytes
扇区大小(逻辑/物理)：512 字节 / 4096 字节
I/O 大小(最小/最佳)：4096 字节 / 4096 字节
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)