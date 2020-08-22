# Linux cfdisk 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux cfdisk 命令用于磁盘分区。

cfdisk 是用来磁盘分区的程序，它十分类似 DOS 的 fdisk，具有互动式操作界面而非传统 fdisk 的问答式界面，您可以轻易地利用方向键来操控分区操作。

### 语法

```
cfdisk [-avz][-c <柱面数目>-h <磁头数目>-s <盘区数目>][-P <r,s,t>][外围设备代号]
```

### 参数说明：

- -a 在程序里不用反白代表选取，而以箭头表示。
- -c<柱面数目> 忽略BIOS的数值，直接指定磁盘的柱面数目。
- -h<磁头数目> 忽略BIOS的数值，直接指定磁盘的磁头数目。
- -P<r,s,t> 显示分区表的内容，附加参数"r"会显示整个分区表的详细资料，附加参数"s"会依照磁区的顺序显示相关信息，附加参数"t"则会以磁头，磁区，柱面的方式来显示资料。
- -s<磁区数目> 忽略BIOS的数值，直接指定磁盘的磁区数目。
- -v 显示版本信息。
- -z 不读取现有的分区，直接当作没有分区的新磁盘使用。

### 实例

进行磁盘分区：

```
[root@localhost trunk (fishserver_simple ✗)]$ cfdisk

                                                     cfdisk (util-linux 2.23.2)

                                                        Disk Drive: /dev/sda
                                                  Size: 42949672960 bytes, 42.9 GB
                                        Heads: 255   Sectors per Track: 63   Cylinders: 5221

      Name                Flags              Part Type         FS Type                    [Label]                  Size (MB)
 -----------------------------------------------------------------------------------------------------------------------------------
                                              Pri/Log          Free Space                                               1.05        *
      sda1                Boot                Primary          xfs                                                   1073.75        *
      sda2                                    Primary          LVM2_member                                          41874.89        *

        [   Help   ]  [   New    ]  [  Print   ]  [   Quit   ]  [  Units   ]  [  Write   ]

```

进行磁盘分区，使用箭头进行操作，而不使用反白表示：

```
cfdisk -a
```

进行磁盘分区，使用箭头进行操作，而不使用反白表示：

```
cfdisk -s 3
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)