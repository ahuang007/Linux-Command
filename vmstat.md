# Linux vmstat 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

vmstat 是Virtual Meomory Statistics（虚拟内存统计）的缩写，可对操作系统的虚拟内存、进程、CPU 活动进行监控。它能够对系统的整体情况进行统计，无法对某个进程进行深入分析。

vmstat 工具提供了一种低开销的系统性能观察方式。

vmstat 属于 sysstat 软件包。可以用 `yum install sysstat` 直接安装。

### (1)用法
用法: vmstat [选项参数]
或 vmstat [选项参数] [数字] [数字]
### (2)功能:
功能: 报告虚拟内存的统计信息,关于进程、内存、I/O等系统整体运行状态。
### (3)选项参数:
1) -d:　　　　　　　　显示磁盘相关统计信息。
2) -a：　　　　　　  显示活跃和非活跃内存
3) -f：　　　　　　　 显示从系统启动至今的fork数量。
4) -p：　　　　　　  显示指定磁盘分区统计信息
5) -s：　　　　　　  显示内存相关统计信息及多种系统活动数量。
6) -m：　　　　　　 显示slabinfo

### (4)实例:

1. **vmstat显示虚拟内存使用情况**

   ```
   [root@localhost test]# vmstat
   procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
    r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
    1  0      0 1075240      0 2561176    0    0     1     8    4    0  0  0 99  0  0
   ```

   字段说明:

   **1.Procs（进程）**

   r: 运行队列中进程数量，这个值也可以判断是否需要增加CPU。（长期大于1）

   b: 等待IO的进程数量。

   **2.Memory（内存）**

   swpd: 使用虚拟内存大小，如果swpd的值不为0，但是SI，SO的值长期为0，这种情况不会影响系统性能。

   free: 空闲物理内存大小。

   buff: 用作缓冲的内存大小。

   cache: 用作缓存的内存大小，如果cache的值大的时候，说明cache处的文件数多，如果频繁访问到的文件都能被cache处，那么磁盘的读IO bi会非常小。

   **3.Swap**

   si: 每秒从交换区写到内存的大小，由磁盘调入内存。

   so: 每秒写入交换区的内存大小，由内存调入磁盘。

   注意:

   内存够用的时候，这2个值都是0，如果这2个值长期大于0时，系统性能会受到影响，磁盘IO和CPU资源都会被消耗。有些朋友看到空闲内存（free）很少的或接近于0时，就认为内存不够用了，不能光看这一点，还要结合si和so，如果free很少，但是si和so也很少（大多时候是0），那么不用担心，系统性能这时不会受到影响的。

   **4.IO（现在的Linux版本块的大小为1kb）**

   bi: 每秒读取的块数

   bo: 每秒写入的块数

   注意:

   随机磁盘读写的时候，这2个值越大（如超出1024k)，能看到CPU在IO等待的值也会越大。

   **5.system（系统）**

   in: 每秒中断数，包括时钟中断。

   cs: 每秒上下文切换数。

   注意：

   上面2个值越大，会看到由内核消耗的CPU时间会越大。

   **6.CPU（以百分比表示）**

   us: 用户进程执行时间百分比(user time) us的值比较高时，说明用户进程消耗的CPU时间多，但是如果长期超50%的使用，那么我们就该考虑优化程序算法或者进行加速。

   sy: 内核系统进程执行时间百分比(system time) sy的值高时，说明系统内核消耗的CPU资源多，这并不是良性表现，我们应该检查原因。

   wa: IO等待时间百分比 wa的值高时，说明IO等待比较严重，这可能由于磁盘大量作随机访问造成，也有可能磁盘出现瓶颈（块操作）。

   id: 空闲时间百分比

2. **每二秒显示一次系统内存的统计信息**

   ```
   procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
    r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
    1  0      0 1075248      0 2561208    0    0     1     8    4    0  0  0 99  0  0
    0  0      0 1075248      0 2561208    0    0     0     0  836 1594  0  0 100  0  0
    0  0      0 1075248      0 2561208    0    0     0     0  817 1577  0  0 99  0  0
    ...
   ```

3. **vmstat每二秒显示一次系统内存的统计信息,总共5次**

   ```
   [root@localhost test]# vmstat 2 5
   procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu-----
    r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st
    1  0      0 1075044      0 2561208    0    0     1     8    4    0  0  0 99  0  0
    0  0      0 1075012      0 2561208    0    0     0     0  742 1507  0  0 100  0  0
    0  0      0 1075028      0 2561208    0    0     0     0  726 1489  0  0 100  0  0
    0  0      0 1075028      0 2561208    0    0     0     0  723 1486  0  0 100  0  0
    0  0      0 1075028      0 2561208    0    0     0     0  726 1483  0  0 100  0  0
   ```

4. **vmstat -d 显示磁盘的信息**

   ```
   
   ```

5. **vmstat -a 显示活跃内存与非活跃内存**

   ```
   [root@localhost test]# vmstat -d
   disk- ------------reads------------ ------------writes----------- -----IO------
          total merged sectors      ms  total merged sectors      ms    cur    sec
   sda   112653    627 13317212  452088 497856  42876 131372632 2070904      0    318
   sr0       18      0    2056      10      0      0       0       0      0      0
   dm-0  111487      0 13298134  456094 540686      0 131367936 2127598      0    319
   ```

6. **vmstat -f 查看系统已经被fork多少次**

   ```
   [root@localhost test]# vmstat -f
         2332813 forks
   ```

7. **vmstat -p tmpfs 查看特定磁盘设备的**

   ```
   [root@localhost test]# vmstat -p /dev/sda1
   sda1          reads   read sectors  writes    requested writes
                   1933      12518         46       4696
   ```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)