# Linux iostat 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

## 概述

iostat是I/O statistics（输入/输出统计）的缩写。

iostat 主要用于输出磁盘IO 和 CPU的统计信息。

iostat属于sysstat软件包。可以用 `yum install sysstat` 直接安装。

## iostat 用法

用法：**iostat [选项] [<时间间隔>] [<次数>]**

## 命令参数：

**-c：** 显示CPU使用情况
 **-d：** 显示磁盘使用情况
 **-N：** 显示磁盘阵列(LVM) 信息
 **-n：** 显示NFS 使用情况
 **-k：** 以 KB 为单位显示
 **-m：** 以 M 为单位显示
 **-t：** 报告每秒向终端读取和写入的字符数和CPU的信息
 **-V：** 显示版本信息
 **-x：** 显示详细信息
 **-p：**[磁盘] 显示磁盘和分区的情况

## 示例

- iostat 

  显示所有设备负载情况

  ```
  [root@localhost ~]# iostat
  Linux 3.10.0-1160.11.1.el7.x86_64 (localhost.localdomain) 	01/25/2021 	_x86_64_	(16 CPU)
  
  avg-cpu:  %user   %nice %system %iowait  %steal   %idle
             0.84    0.00    0.14    0.00    0.00   99.02
  
  Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
  sda               0.82         3.53       138.53    8737105  342406354
  scd0              0.00         0.00         0.00       1028          0
  dm-0              0.86         3.53       138.53    8727518  342403936
  ```

  #### cpu属性值说明：

  **%user：**CPU处在用户模式下的时间百分比。
   **%nice：**CPU处在带NICE值的用户模式下的时间百分比。
   **%system：**CPU处在系统模式下的时间百分比。
   **%iowait：**CPU等待输入输出完成时间的百分比。
   **%steal：**管理程序维护另一个虚拟处理器时，虚拟CPU的无意识等待时间百分比。
   **%idle：**CPU空闲时间百分比。

  > 备注：如果%iowait的值过高，表示硬盘存在I/O瓶颈，%idle值高，表示CPU较空闲，如果%idle值高但系统响应慢时，有可能是CPU等待分配内存，此时应加大内存容量。%idle值如果持续低于10，那么系统的CPU处理能力相对较低，表明系统中最需要解决的资源是CPU。

  #### disk属性值说明：

  磁盘名称
   **device:**磁盘名称
   **tps:**每秒钟发送到的I/O请求数.
   **Blk_read/s:**每秒读取的block数.
   **Blk_wrtn/s:**每秒写入的block数.
   **Blk_read:**读入的block总数.
   **Blk_wrtn:**写入的block总数.

  - iostat 1 5
     间隔1秒，总共显示5次
  - iostat -d 2
     每隔2秒,显示一次设备统计信息.
  - iostat -d 2 3
     每隔2秒,显示一次设备统计信息.总共输出3次.
  - iostat -x sda sdb 2 3
     每隔2秒显示一次sda, sdb两个设备的扩展统计信息,共输出3次.
  - iostat -p sda 2 3
     每隔2秒显示一次sda及上面所有分区的统计信息,共输出3次.

  - iostat -m
     以M为单位显示所有信息

  ```
  [root@localhost ~]# iostat -m
  Linux 3.10.0-1160.11.1.el7.x86_64 (localhost.localdomain) 	01/25/2021 	_x86_64_	(16 CPU)
  
  avg-cpu:  %user   %nice %system %iowait  %steal   %idle
             0.84    0.00    0.14    0.00    0.00   99.02
  
  Device:            tps    MB_read/s    MB_wrtn/s    MB_read    MB_wrtn
  sda               0.82         0.00         0.14       8532     334381
  scd0              0.00         0.00         0.00          1          0
  dm-0              0.86         0.00         0.14       8522     334379
  ```

  * iostat -d sda
    显示指定硬盘信息

  ```
  [root@localhost ~]# iostat -d sda
  Linux 3.10.0-1160.11.1.el7.x86_64 (localhost.localdomain) 	01/25/2021 	_x86_64_	(16 CPU)
  
  Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
  sda               0.82         3.53       138.51    8737105  342407642
  ```

  * iostat -t
    报告每秒向终端读取和写入的字符数。

  ```
  [root@localhost ~]# iostat -t
  Linux 3.10.0-1160.11.1.el7.x86_64 (localhost.localdomain) 	01/25/2021 	_x86_64_	(16 CPU)
  
  01/25/2021 11:14:17 AM
  avg-cpu:  %user   %nice %system %iowait  %steal   %idle
  0.84    0.00    0.14    0.00    0.00   99.02
  
  Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
  sda               0.82         3.53       138.51    8737105  342407811
  scd0              0.00         0.00         0.00       1028          0
  dm-0              0.86         3.53       138.51    8727518  342405393io
  ```

  * iostat -d -k 1 1
    查看TPS和吞吐量信息
  
  ```
  [root@localhost ~]# iostat -d -k 1 1
  Linux 3.10.0-1160.11.1.el7.x86_64 (localhost.localdomain) 	01/25/2021 	_x86_64_	(16 CPU)
  
  Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
  sda               0.82         3.53       138.50    8737105  342407818
  scd0              0.00         0.00         0.00       1028          0
  dm-0              0.86         3.53       138.50    8727518  342405400
  ```
  
  * iostat -d -x -k 1 1
    查看设备使用率（%util）、响应时间（await）
  
  ```
  [root@localhost ~]# iostat -d -x -k 1 1
  Linux 3.10.0-1160.11.1.el7.x86_64 (localhost.localdomain) 	01/25/2021 	_x86_64_	(16 CPU)
  
  Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await r_await w_await  svctm  %util
  sda               0.00     0.05    0.14    0.68     3.53   138.50   347.84     0.00    3.54    2.05    3.85   0.35   0.03
  scd0              0.00     0.00    0.00    0.00     0.00     0.00   114.22     0.00    0.11    0.11    0.00   0.11   0.00
  dm-0              0.00     0.00    0.14    0.72     3.53   138.50   329.55     0.00    3.43    2.09    3.69   0.33   0.03
  ```
  
    说明：
  
  **rrqm/s:**  每秒进行 merge 的读操作数目。即 rmerge/s
   **wrqm/s:**  每秒进行 merge 的写操作数目。即 wmerge/s
   **r/s:**  每秒完成的读 I/O 设备次数。即 rio/s
   **w/s:**  每秒完成的写 I/O 设备次数。即 wio/s
   **rkB/s:**  每秒读K字节数。是 rsect/s 的一半，因为每扇区大小为512字节。
   **wkB/s:**  每秒写K字节数。是 wsect/s 的一半。
   **avgrq-sz:**  平均每次设备I/O操作的数据大小 (扇区)。
   **avgqu-sz:**  平均I/O队列长度。
   **rsec/s:**  每秒读扇区数。即 rsect/s
   **wsec/s:**  每秒写扇区数。即 wsect/s
   **r_await:**每个读操作平均所需的时间
   不仅包括硬盘设备读操作的时间，还包括了在kernel队列中等待的时间。
   **w_await:**每个写操作平均所需的时间
   不仅包括硬盘设备写操作的时间，还包括了在kernel队列中等待的时间。
   **await:** 平均每次设备I/O操作的等待时间 (毫秒)。
   **svctm:** 平均每次设备I/O操作的服务时间 (毫秒)。
   **%util:**  一秒中有百分之多少的时间用于 I/O 操作，即被io消耗的cpu百分比
  
  > 备注：如果 %util 接近 100%，说明产生的I/O请求太多，I/O系统已经满负荷，该磁盘可能存在瓶颈。如果 svctm 比较接近 await，说明 I/O 几乎没有等待时间；如果 await 远大于 svctm，说明I/O 队列太长，io响应太慢，则需要进行必要优化。如果avgqu-sz比较大，也表示有当量io在等待。
  
  * iostat -c 1 2
    查看cpu状态
    间隔1秒显示一次，总共显示2次
  
  ```
  [root@localhost ~]# iostat -c 1 2
  Linux 3.10.0-1160.11.1.el7.x86_64 (localhost.localdomain) 	01/25/2021 	_x86_64_	(16 CPU)
  
  avg-cpu:  %user   %nice %system %iowait  %steal   %idle
  0.84    0.00    0.14    0.00    0.00   99.02
  
  avg-cpu:  %user   %nice %system %iowait  %steal   %idle
  0.00    0.00    0.00    0.00    0.00  100.00
  ```
  

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

