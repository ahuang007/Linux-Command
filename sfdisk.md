# Linux sfdisk命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux sfdisk 命令是硬盘分区工具程序。

sfdisk 为硬盘分区工具程序，可显示分区的设置信息，并检查分区是否正常。

### 语法

```
sfdisk [-?Tvx][-d <硬盘>][-g <硬盘>][-l <硬盘>][-s <分区>][-V <硬盘>]
```

**参数**：

- -?或--help 显示帮助。
- -d<硬盘> 显示硬盘分区的设置。
- -g<硬盘>或--show-geometry<硬盘> 显示硬盘的CHS参数。
- -l<硬盘> 显示后硬盘分区的相关设置。
- -s<分区> 显示分区的大小，单位为区块。
- -T或--list-types 显示所有sfdisk能辨识的文件系统ID。
- -v或--version 显示版本信息。
- -V<硬盘>或--verify<硬盘> 检查硬盘分区是否正常。
- -x或--show-extend 显示扩展分区中的逻辑分区。

### 实例

显示分区信息：

```
[root@localhost test ]$ sfdisk -l

Disk /dev/sda: 5221 cylinders, 255 heads, 63 sectors/track
Units: cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+    130-    131-   1048576   83  Linux
/dev/sda2        130+   5221-   5091-  40893440   8e  Linux LVM
/dev/sda3          0       -       0          0    0  Empty
/dev/sda4          0       -       0          0    0  Empty

Disk /dev/mapper/centos-root: 5090 cylinders, 255 heads, 63 sectors/track
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)