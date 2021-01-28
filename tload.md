# Linux tload 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux tload 命令用于显示系统负载状况。

tload 指令使用 ASCII 字符简单地以文字模式显示系统负载状态。假设不给予终端机编号，则会在执行 tload 指令的终端机显示负载情形。

### 语法

```
tload [-V][-d <间隔秒数>][-s <刻度大小>][终端机编号]
```

**参数说明**：

- -d<间隔秒数> 　设置tload检测系统负载的间隔时间，单位以秒计算。
- -s<刻度大小> 　设置图表的垂直刻度大小，单位以列计算。
- -V 　显示版本信息。

### 实例

显示系统负载

```
[root@localhost TransferServer]# tload
 0.00, 0.02, 0.05 
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)