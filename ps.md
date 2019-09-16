# Linux ps 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`ps = process status `

Linux ps 命令用于显示当前进程 (process) 的状态。

### 语法

```
ps [options] [--help]
```

**参数**：

- ps 的参数非常多, 在此仅列出几个常用的参数并大略介绍含义
- -A 列出所有的行程
- -w 显示加宽可以显示较多的资讯
- -au 显示较详细的资讯
- -aux 显示所有包含其他使用者的行程
- au(x) 输出格式 :
- USER PID %CPU %MEM VSZ RSS TTY STAT START TIME COMMAND
- USER: 行程拥有者
- PID: pid
- %CPU: 占用的 CPU 使用率
- %MEM: 占用的记忆体使用率
- VSZ: 占用的虚拟记忆体大小
- RSS: 占用的记忆体大小
- TTY: 终端的次要装置号码 (minor device number of tty)
- STAT: 该行程的状态:
- D: 无法中断的休眠状态 (通常 IO 的进程)
- R: 正在执行中
- S: 静止状态
- T: 暂停执行
- Z: 不存在但暂时无法消除
- W: 没有足够的记忆体分页可分配
- <: 高优先序的行程
- N: 低优先序的行程
- L: 有记忆体分页分配并锁在记忆体内 (实时系统或捱A I/O)
- START: 行程开始时间
- TIME: 执行的时间
- COMMAND:所执行的指令

### 实例

```
[root@server test ]$ ps -A # 显示进程信息
PID TTY     TIME CMD
  1 ?        00:00:01 init
  2 ?        00:00:00 kthreadd
  3 ?        00:00:00 migration/0
  4 ?        00:00:00 ksoftirqd/0
  5 ?        00:00:00 stopper/0
  6 ?        00:00:00 watchdog/0
  7 ?        00:00:00 migration/1
  8 ?        00:00:00 stopper/1
  9 ?        00:00:00 ksoftirqd/1
 10 ?        00:00:00 watchdog/1
 11 ?        00:00:01 events/0
...
```

显示指定用户信息

```
[root@server test ]$ ps -u root # 显示root进程用户信息
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 stopper/0
    6 ?        00:00:00 watchdog/0
    7 ?        00:00:00 migration/1
    8 ?        00:00:00 stopper/1
    9 ?        00:00:00 ksoftirqd/1
   10 ?        00:00:00 watchdog/1
   11 ?        00:00:01 events/0
   ...
```

显示所有进程信息，连同命令行

```
[root@server test ]$ ps -ef  # 显示所有命令，连带命令行
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 09:55 ?        00:00:01 /sbin/init
root         2     0  0 09:55 ?        00:00:00 [kthreadd]
root         3     2  0 09:55 ?        00:00:00 [migration/0]
root         4     2  0 09:55 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 09:55 ?        00:00:00 [stopper/0]
root         6     2  0 09:55 ?        00:00:00 [watchdog/0]
root         7     2  0 09:55 ?        00:00:00 [migration/1]
root         8     2  0 09:55 ?        00:00:00 [stopper/1]
root         9     2  0 09:55 ?        00:00:00 [ksoftirqd/1]
root        10     2  0 09:55 ?        00:00:00 [watchdog/1]
root        11     2  0 09:55 ?        00:00:01 [events/0]
...
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)