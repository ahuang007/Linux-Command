# Linux strace 命令

## 一、说明

 **strace **是 Linux 中一个调试和跟踪工具。它可以接管被跟踪进程执行的系统调用和收到的信号。然后把每一个执行的系统调用的名字，参数和返回值打印出来。可以通过 strace 找到问题出现在 user 层还是 kernel 层。strace 显示这些调用的参数并返回符号形式的值。strace 从内核接收信息，而且不需要以任何特殊的方式来构建内核。

```
strace命令是一个集诊断、调试、统计于一体的工具，使用strace对应用的系统调用和信号传递的跟踪结果来对应用进行分析 ，以达到解决问题或者了解应用工作过程的目的。有时错误日志不能满足定位问题的需求，因此需要从更“深层”的方面着手分析，可以通过strace观察这些系统调用及其参数、返回值，界定出错的范围，甚至找出问题出现的根因。
```

- 操作系统内核直接运行在硬件上，提供设备管理、内存管理、任务调度等功能。
- 用户空间通过API请求内核空间的服务来完成其功能——内核提供给用户空间的这些API, 就是系统调用。

进程不能直接访问硬件设备，当进程需要访问硬件设备(比如读取磁盘文件，接收网络数据等等)时，必须由**用户态**模式切换至**内核态**模式，通过系统调用访问硬件设备。strace 可以跟踪到一个进程产生的系统调用,包括参数，返回值，执行消耗的时间。 对于运维的问题定位，strace 工具结合系统调用表，就能解决绝大多数问题。 strace 工具比较高级的用途：

 1）可以对特定的系统调用或者几组系统调用进行过滤

 2）可以通过统计特定系统调用的调用次数、耗费的时间、成功和失败的次数来配置(profile)系统调用的使用

 3）可以跟踪发送给进程的信号量

 4）可以通过pid附着(attach)到任何运行的进程

Linux内核目前有300多个系统调用，详细的列表可以通过syscalls手册页查看。这些系统调用主要分为几类：

1）文件和设备访问类 比如 open/close/read/write/chmod 等
2）进程管理类 fork/clone/execve/exit/getpid 等
3）信号类 signal/sigaction/kill 等
4）内存管理 brk/mmap/mlock 等
5）进程间通信 IPC shmget/semget * 信号量，共享内存，消息队列等
6）网络通信 socket/connect/sendto/sendmsg 等
7）其他

## 二、用法

### 2.1 strace有两种运行模式

1. 一种是通过它启动要跟踪的进程 ，在原本的命令前加上strace即可 ，例如：要跟踪 “ls -lh /var/log/messages” 这个命令的执行，可以这样：

```
[root@localhost ~]# strace ls -a
execve("/usr/bin/ls", ["ls", "-a"], 0x7ffc68b23e88 /* 25 vars */) = 0
brk(NULL)                               = 0x78e000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcabefb7000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=30853, ...}) = 0
mmap(NULL, 30853, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fcabefaf000
close(3)                                = 0
......
```

2. 另外一种运行模式，是跟踪已经在运行的进程，在不中断进程执行的情况下， 即可查看进程的运行情况，给 strace 传递 -p pid 选项。例如：有个在运行的some_server 服务，第一步，查看 pid:

```
[root@localhost accountserver]# pidof skynet
2318
```

依据 pid 用 strace 跟踪其执行:

```
[root@localhost accountserver]# strace -p 2318
strace: Process 2318 attached
futex(0x7fdbcfffb9d0, FUTEX_WAIT, 2319, NULL
```

完成跟踪时，按 `ctrl + C` 结束 strace 即可。

### 2.2 strace的常用选项

```
-c 统计每一系统调用的所执行的时间,次数和出错的次数等. 
-d 输出strace关于标准错误的调试信息. 
-f 除了跟踪当前进程外，还跟踪由fork调用所产生的子进程. 
-ff 如果提供-o filename,则所有进程的跟踪结果输出到相应的filename.pid中,pid是各进程的进程号. 
-F 尝试跟踪vfork调用.在-f时,vfork不被跟踪. 
-h 输出简要的帮助信息. 
-i 输出系统调用的入口指针寄存器值. 
-q 禁止输出关于结合(attaching)、脱离(detaching)的消息，当输出重定向到一个文件时，自动抑制此类消息. 
-r 打印出相对时间关于每一个系统调用，即连续的系统调用起点之间的时间差，与-t对应. 
-t 打印各个系统调用被调用时的绝对时间秒级，观察程序各部分的执行时间可以用此选项。 
-tt 在输出中的每一行前加上时间信息,微秒级. 
-ttt 在每行输出前添加相对时间信息，格式为”自纪元时间起经历的秒数.微秒数”
-T 显示每一调用所耗的时间，其时间开销在输出行最右侧的尖括号内. 
-v 冗余显示模式：显示系统调用中argv[]envp[]stat、termio(s)等数组/结构体参数所有的元素/成员内容. 
-V 输出strace的版本信息. 
-x 以十六进制形式输出非标准字符串 。
-xx 所有字符串以十六进制形式输出. 
-a column 设置返回值的输出位置.默认为40，即"="出现在第40列.
-e expr 指定一个表达式,用来控制如何跟踪.
    -e trace=set 只跟踪指定的系统 调用.例如:-e trace=open.
    -e trace=file 只跟踪有关文件操作的系统调用. 
    -e trace=process 只跟踪有关进程控制的系统调用. 
    -e trace=network 跟踪与网络有关的所有系统调用. 
    -e trace=signal 跟踪所有与系统信号有关的 系统调用 
    -e trace=ipc 跟踪所有与进程通讯有关的系统调用 
    -e abbrev=set 设定 strace输出的系统调用的结果集.-v 等与 abbrev=none.默认为abbrev=all. 
    -e raw=set 将指 定的系统调用的参数以十六进制显示. 
    -e signal=set 指定跟踪的系统信号.默认为all.如signal=!SIGIO,表示不跟踪SIGIO信号. 
    -e read=set 输出从指定文件中读出 的数据.例如: -e read=3,5 -e write=set 
-E var 从命令的环境变量列表中移除var。
-E var=val 将var=val放入命令的环境变量列表.
-o filename 将strace的输出写入文件filename，而不是显示到标准错误输出（stderr）.
-p pid 跟踪指定的进程pid，可指定多达32个(-p pid)选项以同时跟踪多个进程。该选项常用于调试后台进程. 
-s strsize 限制每行输出中字符串(如read参数)的最大显示长度，默认32字节。但文件名总是完整显示
-S sortby 按指定规则对-c选项的输出直方图进行排序。sortby取值可为time、calls、name和nothing(默认     time)
-u username 以username 的UID和GID执行被跟踪的命令
123456789101112131415161718192021222324252627282930313233343536
```

 以上部分参数可组合使用，如：

```
[root@localhost accountserver]# strace -o output.txt -T -tt -e trace=all -p 2318
strace: Process 2318 attached
```

 表示的含义是，跟踪 2318 进程的所有系统调用（-e trace=all），并统计系统调用的花费时间，以及开始时间（并以可视化的时分秒格式显示），最后将记录结果存在output.txt文件里面。

 strace 记录程序所产生的每次系统调用，并以类似 C 的格式(无论创建该程序时使用何种编程语言)各自显示为单独的一行。每行起始为系统调用的函数名，括号内为参数，该调用的返回值则显示在等号右侧。当参数为数组或结构体时，显示其元素(方括号)或成员(花括号)内容，见 execve 和 fstat64。当参数为 bit 时，使用方括号并用空格隔开每项参数，如：

 `sigprocmask(SIG_BLOCK,[CHLD TTOU],[ ]) = 0`

 第二个参数代表信号SIGCHLD和SIGTTOU；若bit型参数全部置位，则输出如:

 `sigprocmask(SIG_UNBLOCK,~[ ],NULL) = 0`

此处第二个参数全部置位。

## 三、strace使用案例

### 3.1 跟踪程序运行

strace 用法举例，测试程序 test1.c 运行过程中的系统调用情况：

```
#include <stdio.h>
int main(void)
{
    fputs("hello", stdout);
    sleep(2);
    //这里一开始输出了换行符，所以前面的hello就被输出到屏幕上了。
    fputs("\nworld\n", stdout);
    sleep(2);
    return 0;
}

[root@localhost test]# gcc test2.c -o test2
[root@localhost test]# strace ./test2
execve("./test2", ["./test2"], 0x7ffdb0e1bd20 /* 26 vars */) = 0
brk(NULL)                               = 0x258e000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f55c179c000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=27410, ...}) = 0
mmap(NULL, 27410, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f55c1795000
close(3)                                = 0
open("/lib64/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`&\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=2156272, ...}) = 0
mmap(NULL, 3985920, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f55c11ae000
mprotect(0x7f55c1372000, 2093056, PROT_NONE) = 0
mmap(0x7f55c1571000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c3000) = 0x7f55c1571000
mmap(0x7f55c1577000, 16896, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f55c1577000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f55c1794000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f55c1792000
arch_prctl(ARCH_SET_FS, 0x7f55c1792740) = 0
mprotect(0x7f55c1571000, 16384, PROT_READ) = 0
mprotect(0x600000, 4096, PROT_READ)     = 0
mprotect(0x7f55c179d000, 4096, PROT_READ) = 0
munmap(0x7f55c1795000, 27410)           = 0
fstat(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f55c179b000
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGCHLD, NULL, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
nanosleep({tv_sec=2, tv_nsec=0}, 0x7ffcaec33dc0) = 0
write(1, "hello\nworld\n", 12hello
world
)          = 12
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGCHLD, NULL, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
nanosleep({tv_sec=2, tv_nsec=0}, 0x7ffcaec33dc0) = 0
exit_group(0)                           = ?
+++ exited with 0 +++
```

 第3行表示通过系统调用 execve 来建立一个进程，本例中为 test2 对应的进程，在控制台中执行各种命令，比如 ls、cd 时，都是通过系统调用 execve 来建立它们的进程的，通过 strace 可以看到程序运行的细节。

 第4行 brk 通过传递的 addr 来重新设置 program break，成功则返回0，否则返回-1。 brk(0) 的参数是一个地址，假如已经知道了堆的起始地址，还有堆的大小，那么就可以据此修改 brk() 中的地址参数已达到调整堆的目的。以0作为参数调用 brk，返回值为内存管理的起始地址(若在子进程中调用 malloc，则从0x8a92000地址开始分配空间)

 第6~8行表示打开动态连接库的过程，如果程序是静态连接的，这几个步骤将不需要。

 第14~19行是程序的处理过程，nanosleep() 使得进程进入睡眠状态,指定时候后唤醒进程,sleep()基于其实现 ，然后写入hello 和 world。

 20~21行表示退出进程中所有的线程。

 加入-c选项，可以打印调用了哪些系统函数，调用多少次数，消耗了多少时间等信息 ，用于性能分析。

```
[root@localhost test]# strace -c ./test2
hello
world
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
  0.00    0.000000           0         1           read
  0.00    0.000000           0         1           write
  0.00    0.000000           0         2           open
  0.00    0.000000           0         2           close
  0.00    0.000000           0         3           fstat
  0.00    0.000000           0         8           mmap
  0.00    0.000000           0         4           mprotect
  0.00    0.000000           0         1           munmap
  0.00    0.000000           0         1           brk
  0.00    0.000000           0         2           rt_sigaction
  0.00    0.000000           0         4           rt_sigprocmask
  0.00    0.000000           0         1         1 access
  0.00    0.000000           0         2           nanosleep
  0.00    0.000000           0         1           execve
  0.00    0.000000           0         1           arch_prctl
------ ----------- ----------- --------- --------- ----------------
100.00    0.000000                    34         1 total
```

### 3.2 分析程序挂死原因

 test3.c 代码使用死循环模拟用户态挂死，调用sleep模拟内核态程序挂死，然后利用strace工具分析原因。

```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include <string.h>

int main(int argc, char** argv)
{
    getpid(); //该系统调用起到标识作用
    if(argc < 2)
    {
        printf("hang (user|system)\n");
        return 1;
    }
    if(!strcmp(argv[1], "user"))
        while(1);
    else if(!strcmp(argv[1], "system"))
        sleep(500);
    return 0;
}

[root@localhost test]# gcc -o test3 test3.c
[root@localhost test]# strace ./test3 system
execve("./test3", ["./test3", "system"], 0x7ffc87ed7f28 /* 26 vars */) = 0
brk(NULL)                               = 0x1176000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2b8a09c000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=27410, ...}) = 0
mmap(NULL, 27410, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f2b8a095000
close(3)                                = 0
open("/lib64/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`&\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=2156272, ...}) = 0
mmap(NULL, 3985920, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f2b89aae000
mprotect(0x7f2b89c72000, 2093056, PROT_NONE) = 0
mmap(0x7f2b89e71000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c3000) = 0x7f2b89e71000
mmap(0x7f2b89e77000, 16896, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f2b89e77000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2b8a094000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2b8a092000
arch_prctl(ARCH_SET_FS, 0x7f2b8a092740) = 0
mprotect(0x7f2b89e71000, 16384, PROT_READ) = 0
mprotect(0x600000, 4096, PROT_READ)     = 0
mprotect(0x7f2b8a09d000, 4096, PROT_READ) = 0
munmap(0x7f2b8a095000, 27410)           = 0
getpid()                                = 6476
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGCHLD, NULL, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
nanosleep({tv_sec=500, tv_nsec=0}, 

```

 第3行，调用 read，从 /lib/i386-linux-gnu/libc.so.6 该 libc 库文件中读取 832bytes，即读取 ELF 头信息 。

 分析：用户态挂死情况下，strace 在 getpid() 一行输出之后没有其他系统调用输出；进程在内核态挂死，最后一行的系统调用 nanosleep 不能完整显示，这里nanosleep 没有返回值表示该调用尚未完成。

 结论：使用 strace 跟踪挂死程序，如果最后一行系统调用显示完整，程序在逻辑代码处挂死；如果最后一行系统调用显示不完整，程序在该系统调用处挂死。 当程序挂死在系统调用处，可以查看相应系统调用的 man 手册，了解在什么情况下该系统调用会出现挂死情况。

### 3.3 跟踪查看依赖库问题

 strace 帮助查看库依赖问题。

```
[root@localhost test]# strace -o whoami.strace whoami
root
[root@localhost test]# ls
test3  test3.c  whoami.strace
[root@localhost test]# cat whoami.strace 
execve("/usr/bin/whoami", ["whoami"], 0x7ffed2921e80 /* 26 vars */) = 0
brk(NULL)                               = 0x1965000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f1e771c4000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=27410, ...}) = 0
mmap(NULL, 27410, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f1e771bd000
close(3)                                = 0
open("/lib64/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`&\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=2156272, ...}) = 0
mmap(NULL, 3985920, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f1e76bd6000
mprotect(0x7f1e76d9a000, 2093056, PROT_NONE) = 0
mmap(0x7f1e76f99000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c3000) = 0x7f1e76f99000
mmap(0x7f1e76f9f000, 16896, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f1e76f9f000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f1e771bc000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f1e771ba000
arch_prctl(ARCH_SET_FS, 0x7f1e771ba740) = 0
mprotect(0x7f1e76f99000, 16384, PROT_READ) = 0
mprotect(0x605000, 4096, PROT_READ)     = 0
mprotect(0x7f1e771c5000, 4096, PROT_READ) = 0
munmap(0x7f1e771bd000, 27410)           = 0
brk(NULL)                               = 0x1965000
brk(0x1986000)                          = 0x1986000
brk(NULL)                               = 0x1986000
open("/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=106176928, ...}) = 0
mmap(NULL, 106176928, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f1e70693000
close(3)                                = 0
geteuid()                               = 0
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_UNIX, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_UNIX, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
open("/etc/nsswitch.conf", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=1949, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f1e771c3000
read(3, "#\n# /etc/nsswitch.conf\n#\n# An ex"..., 4096) = 1949
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x7f1e771c3000, 4096)            = 0
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=27410, ...}) = 0
mmap(NULL, 27410, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f1e771bd000
close(3)                                = 0
open("/lib64/libnss_files.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260!\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=61560, ...}) = 0
mmap(NULL, 2173048, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f1e70480000
mprotect(0x7f1e7048c000, 2093056, PROT_NONE) = 0
mmap(0x7f1e7068b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xb000) = 0x7f1e7068b000
mmap(0x7f1e7068d000, 22648, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f1e7068d000
close(3)                                = 0
mprotect(0x7f1e7068b000, 4096, PROT_READ) = 0
munmap(0x7f1e771bd000, 27410)           = 0
open("/etc/passwd", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=1168, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f1e771c3000
read(3, "root:$6$OMnyJVs5$Nk9bQar2nbS/ylE"..., 4096) = 1168
close(3)                                = 0
munmap(0x7f1e771c3000, 4096)            = 0
fstat(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f1e771c3000
write(1, "root\n", 5)                   = 5
close(1)                                = 0
munmap(0x7f1e771c3000, 4096)            = 0
close(2)                                = 0
exit_group(0)                           = ?
+++ exited with 0 +++
```

 第5行，对于命令行下执行的程序，execve (或 exec 系列调用中的某一个)均为 strace 输出系统调用中的第一个。strace 首先调用 fork 或 clone 函数新建一个子进程，然后在子进程中调用 exec 载入需要执行的程序(这里为 whoami) ；

 第6行，以0作为参数调用 brk，返回值为内存管理的起始地址(若在子进程中调用 malloc，则从0x21d4000地址开始分配空间) ；

 第7行，调用 access 函数检验 /etc/ld.so.nohwcap 是否存在 ；

 第8行，使用 mmap 函数进行匿名内存映射，以此来获取8192bytes内存空间，该空间起始地址为0x7f1519345000，匿名内存映射就是不涉及具体的文件名,避免了文件的创建及打开,很显然只能用于具有亲缘关系的进程间通信 。

 第10行，调用 open 函数尝试打开 /etc/ld.so.cache 文件，返回文件描述符为3 。

 第11行，fstat 函数获取 /etc/ld.so.cache 文件信息 。

 第12行，调用 mmap 函数将 /etc/ld.so.cache 文件映射至内存 。

 第13行，close 关闭文件描述符为3指向的 /etc/ld.so.cache 文件 。

 第18行，使用 mprotect 函数对0x7f1519347000,起始的4096bytes空间进行保护(PROT_NONE 参数就是不能访问，对应还有 PROT_READ 表示可以读取) 。

 第19行，调用 munmap 函数，将 /etc/ld.so.cache 文件从内存中去映射，与8行的 mmap 函数对应 。

### 3.4 跟踪程序退出的系统调用

 利用 strace 跟踪观察程序正常退出时的系统调用情况

```
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv) {
       exit(1);
}

[root@localhost test]# gcc -o test4 test4.c
[root@localhost test]# strace -tt -e trace=process -f ./test4
12:02:48.875760 execve("./test4", ["./test4"], 0x7ffde8c892e0 /* 26 vars */) = 0
12:02:48.877562 arch_prctl(ARCH_SET_FS, 0x7f2992a64740) = 0
12:02:48.878162 exit_group(1)           = ?
12:02:48.878351 +++ exited with 1 +++
```

 -e trace=process 表示只跟踪和进程管理相关的系统调用。

 进程自己退出时（调用 exit 函数，或者从 main 函数返回）, 最终调用的是 exit_group 系统调用， 并且 strace 会输出 exited with X（X为退出码）。

 因为这里的exit函数不是系统调用，而是 glibc 库提供的一个函数，exit 函数的调用最终会转化为 exit_group 系统调用，它会退出当前进程的所有线程。实际上，有一个叫做 _exit() 的系统调用, 线程退出时最终会调用它。

### 3.5 定位共享内存异常

 当遇到服务启动时报错：

```
shmget 267264 30097568: Invalid argument
Can not get shm...exit!
12
```

错误日志提示获取共享内存出错，通过strace看下 ：

```
[root@localhost test]# strace -tt -f -e trace=ipc ./a_mon_svr     ../conf/a_mon_svr.conf
22:46:36.351798 shmget(0x5feb, 12000, 0666) = 0
22:46:36.351939 shmat(0, 0, 0)          = ?
Process 21406 attached
22:46:36.355439 shmget(0x41400, 30097568, 0666) = -1 EINVAL (Invalid argument)
shmget 267264 30097568: Invalid argument
Can not get shm...exit!
1234567
```

通过-e trace=ipc 选项，让 strace 只跟踪和进程通信相关的系统调用。

从 strace 输出得知是 shmget 系统调用出错了，errno 是 EINVAL。同样， 查询下 shmget 手册页，搜索EINVAL的错误码的说明:

> EINVAL A new segment was to be created and size < SHMMIN or size > SHMMAX, or no new segment was to be created, a segment with given key existed, but size is greater than the size of that segment

shmget 设置EINVAL错误码的原因为下列之一：

- 要创建的共享内存段比 SHMMIN 小 (一般是1个字节)
- 要创建的共享内存段比 SHMMAX 大 (内核参数 kernel.shmmax 配置)
- 指定 key 的共享内存段已存在，其大小和调用 shmget 时传递的值不同。

从 strace 输出看，要连的共享内存 key 0x41400, 指定的大小是30097568字节，明显与第1、2种情况不匹配。那只剩下第三种情况。使用 ipcs 看下是否真的是大小不匹配：

```
ipcs  -m | grep 41400
key        shmid      owner      perms      bytes      nattch     status    
0x00041400 1015822    root       666        30095516   1
123
```

 可以看到，已经0x41400这个key已经存在，并且其大小为30095516字节，和我们调用参数中的30097568不匹配，于是产生了这个错误。在这个案例里面，导致共享内存大小不一致的原因，是一组程序中，其中一个编译为32位，另外一个编译为64位,代码里面使用了 long 这个变长int数据类型。

 注意：当目标进程卡死在用户态时，strace 会没有输出 ，此时需要其他的跟踪手段，比如 gdb/perf/SystemTap 等。

