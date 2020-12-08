# Linux free 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux free 命令用于显示内存状态。

free 指令会显示内存的使用情况，包括实体内存，虚拟的交换文件内存，共享内存区段，以及系统核心使用的缓冲区等。

### 语法

```
free [-bkmotV][-s <间隔秒数>]
```

**参数说明**：

- -b 　以Byte为单位显示内存使用情况。

- -k 　以KB为单位显示内存使用情况。

- -m 　以MB为单位显示内存使用情况。

- -h 　以合适的单位显示内存使用情况，最大为三位数，自动计算对应的单位值。单位有：

  ```
  B = bytes
  K = kilos
  M = megas
  G = gigas
  T = teras
  ```

- -o 　不显示缓冲区调节列。

- -s<间隔秒数> 　持续观察内存使用状况。

- -t 　显示内存总和列。

- -V 　显示版本信息。

### 实例

显示内存使用情况

```
[root@localhost ~]# free //显示内存使用信息
[root@localhost ~]# free
              total        used        free      shared  buff/cache   available
Mem:        4045140      357628      642852      205720     3044660     3192140
Swap:             0           0           0

```

以总和的形式显示内存的使用信息

```
[root@localhost ~]# free -t //以总和的形式查询内存的使用信息
              total        used        free      shared  buff/cache   available
Mem:        4045140      357640      642836      205720     3044664     3192144
Swap:             0           0           0
Total:      4045140      357640      642836

```

周期性的查询内存使用信息

```
[root@localhost ~]# free -s 3 //每3s 执行一次命令
              total        used        free      shared  buff/cache   available
Mem:        4045140      357692      642784      205720     3044664     3192092
Swap:             0           0           0

              total        used        free      shared  buff/cache   available
Mem:        4045140      357708      642768      205720     3044664     3192076
Swap:             0           0           0
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)