# Linux badblocks 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux badblocks 命令用于检查磁盘装置中损坏的区块。

执行指令时须指定所要检查的磁盘装置，及此装置的磁盘区块数。

### 语法

```
badblocks [-svw][-b <区块大小>][-o <输出文件>][磁盘装置][磁盘区块数][启始区块]
```

**参数说明**：

- -b<区块大小> 指定磁盘的区块大小，单位为字节。
- -o<输出文件> 将检查的结果写入指定的输出文件。
- -s 在检查时显示进度。
- -v 执行时显示详细的信息。
- -w 在检查时，执行写入测试。
- [磁盘装置] 指定要检查的磁盘装置。
- [磁盘区块数] 指定磁盘装置的区块总数。
- [启始区块] 指定要从哪个区块开始检查。

### 实例

查看系统当前硬盘信息。

```
[root@localhost test ]$ fdisk -l

Disk /dev/sda: 42.9 GB, 42949672960 bytes, 83886080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk label type: dos
Disk identifier: 0x000ead1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     2099199     1048576   83  Linux
/dev/sda2         2099200    83886079    40893440   8e  Linux LVM

Disk /dev/mapper/centos-root: 41.9 GB, 41871736832 bytes, 81780736 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

```

通过命令扫描硬盘。

```
[root@localhost test ]$ badblocks -s -v /dev/sda2
Checking blocks 0 to 40893439
Checking for bad blocks (read-only test): done                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)
其中，“0 bad blocks found”表示硬盘存在0个坏块。
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)