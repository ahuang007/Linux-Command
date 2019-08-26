# Linux top 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux top 命令用于实时显示 process 的动态。

使用权限：所有使用者。

### 语法

```
top [-] [d delay] [q] [c] [S] [s] [i] [n] [b]
```

**参数说明**：

- d : 改变显示的更新速度，或是在交谈式指令列( interactive command)按 s
- q : 没有任何延迟的显示速度，如果使用者是有 superuser 的权限，则 top 将会以最高的优先序执行
- c : 切换显示模式，共有两种模式，一是只显示执行档的名称，另一种是显示完整的路径与名称S : 累积模式，会将己完成或消失的子行程 ( dead child process ) 的 CPU time 累积起来
- s : 安全模式，将交谈式指令取消, 避免潜在的危机
- i : 不显示任何闲置 (idle) 或无用 (zombie) 的行程
- n : 更新的次数，完成后将会退出 top
- b : 批次档模式，搭配 "n" 参数一起使用，可以用来将 top 的结果输出到档案内

### 实例

显示进程信息

```
[root@server StressTest ]$ top                         
top - 09:52:56 up 19 min,  2 users,  load average: 0.06, 0.03, 0.02
Tasks: 207 total,   1 running, 206 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.5%sy,  0.1%ni, 97.8%id,  1.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1913608k total,   835572k used,  1078036k free,    86660k buffers
Swap:  4095996k total,        0k used,  4095996k free,   246928k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                       
 3652 root      30  10  163m  31m 4880 S  2.0  1.7   0:01.40 slideshow                                                                                                      
 3835 root      20   0  170m  29m 1896 S  2.0  1.6   0:00.46 skynet                                                                                                         
    1 root      20   0 19316 1588 1264 S  0.0  0.1   0:01.31 init                                                                                                           
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.01 kthreadd                                                                                                       
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.01 migration/0                                                                                                    
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                                                                    
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 stopper/0                                                                                                      
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0           
```

显示完整命令

```
[root@server StressTest ]$ top -c
top - 09:53:22 up 19 min,  2 users,  load average: 0.04, 0.03, 0.01
Tasks: 207 total,   1 running, 206 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.5%sy,  0.1%ni, 97.9%id,  1.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1913608k total,   835676k used,  1077932k free,    86660k buffers
Swap:  4095996k total,        0k used,  4095996k free,   246928k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                       
 3835 root      20   0  172m  29m 1896 S  3.9  1.6   0:00.93 /root/StressTest/sh/../skynet/skynet /root/StressTest/sh/config.redis                                          
 3879 root      20   0 15144 1236  856 R  2.0  0.1   0:00.01 top -c                                                                                                         
    1 root      20   0 19316 1588 1264 S  0.0  0.1   0:01.31 /sbin/init                                                                                                     
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.01 [kthreadd]                                                                                                     
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.01 [migration/0]                                                                                                  
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.01 [ksoftirqd/0]                                                                                                  
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 [stopper/0]                                                                                                    
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 [watchdog/0]                                                                                                   
    7 root      RT   0     0    0    0 S  0.0  0.0   0:00.01 [migration/1]                                                                                                  
    8 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 [stopper/1]                                                                                                    
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 [ksoftirqd/1]                                                                                                  
   10 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 [watchdog/1]                 
```

以批处理模式显示程序信息

```
[root@server StressTest ]$ top -b
top - 09:53:39 up 19 min,  2 users,  load average: 0.03, 0.02, 0.01
Tasks: 207 total,   1 running, 206 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.5%sy,  0.1%ni, 97.9%id,  1.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1913608k total,   835808k used,  1077800k free,    86672k buffers
Swap:  4095996k total,        0k used,  4095996k free,   246932k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                        
 3835 root      20   0  172m  29m 1896 S  2.0  1.6   0:01.24 skynet                                                                                                         
 3896 root      20   0 14996 1204  848 R  2.0  0.1   0:00.01 top                                                                                                            
    1 root      20   0 19316 1588 1264 S  0.0  0.1   0:01.31 init                                                                                                           
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.01 kthreadd                                                                                                       
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.01 migration/0                                                                                                    
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0                                                                                                    
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 stopper/0                                                                                                      
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0   
```

以累积模式显示程序信息

```
[root@server StressTest ]$ top -S
```

设置信息更新次数

```
[root@server StressTest ]$ top -n 2
//表示更新两次后终止更新显示
```

设置信息更新时间

```
[root@server StressTest ]$ top -d 3
//表示更新周期为3秒
```

显示指定的进程信息

```
[root@server StressTest ]$ top -p 3835
top - 09:56:11 up 22 min,  2 users,  load average: 0.00, 0.01, 0.00
Tasks:   1 total,   0 running,   1 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.1%us,  0.2%sy,  0.3%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   1913608k total,   845696k used,  1067912k free,    86672k buffers
Swap:  4095996k total,        0k used,  4095996k free,   246932k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                       
 3835 root      20   0  172m  40m 1896 S  1.7  2.1   0:03.54 skynet 

//显示进程号为3835的进程信息，CPU、内存占用率等
```

显示更新十次后退出

```
[root@server StressTest ]$ top -n 10
```

使用者将不能利用交谈式指令来对行程下命令

```
[root@server StressTest ]$ top -s
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)