# Linux time 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux time 命令的用途，在于量测特定指令执行时所需消耗的时间及系统资源等资讯。

例如 CPU 时间、记忆体、输入输出等等。需要特别注意的是，部分资讯在 Linux 上显示不出来。这是因为在 Linux 上部分资源的分配函式与 time 指令所预设的方式并不相同，以致于 time 指令无法取得这些资料。

### 语法

```
time [options] COMMAND [arguments]
```

**参数**：

- -o 或 --output=FILE：设定结果输出档。这个选项会将 time 的输出写入 所指定的档案中。如果档案已经存在，系统将覆写其内容。
- -a 或 --append：配合 -o 使用，会将结果写到档案的末端，而不会覆盖掉原来的内容。
- -f FORMAT 或 --format=FORMAT：以 FORMAT 字串设定显示方式。当这个选项没有被设定的时候，会用系统预设的格式。不过你可以用环境变数 time 来设定这个格式，如此一来就不必每次登入系统都要设定一次。

**time 指令可以显示的资源有四大项，分别是**：

- Time resources
- Memory resources
- IO resources
- Command info

**详细的内容如下**：

1、Time Resources

E 执行指令所花费的时间，格式是：[hour]:minute:second。请注意这个数字并不代表实际的 CPU 时间。

e 执行指令所花费的时间，单位是秒。请注意这个数字并不代表实际的 CPU 时间。

S 指令执行时在核心模式（kernel mode）所花费的时间，单位是秒。

U 指令执行时在使用者模式（user mode）所花费的时间，单位是秒。

P 执行指令时 CPU 的占用比例。其实这个数字就是核心模式加上使用者模式的 CPU 时间除以总时间。

2、Memory Resources

M 执行时所占用的实体记忆体的最大值。单位是 KB

t 执行时所占用的实体记忆体的平均值，单位是 KB

K 执行程序所占用的记忆体总量（stack+data+text）的平均大小，单位是 KB

D 执行程序的自有资料区（unshared data area）的平均大小，单位是 KB

p 执行程序的自有堆叠（unshared stack）的平均大小，单位是 KB

X 执行程序间共享内容（shared text）的平均值，单位是 KB

Z 系统记忆体页的大小，单位是 byte。对同一个系统来说这是个常数

3、IO Resources

F 此程序的主要记忆体页错误发生次数。所谓的主要记忆体页错误是指某一记忆体页已经置换到置换档（swap file)中，而且已经分配给其他程序。此时该页的内容必须从置换档里再读出来。

R 此程序的次要记忆体页错误发生次数。所谓的次要记忆体页错误是指某一记忆体页虽然已经置换到置换档中，但尚未分配给其他程序。此时该页的内容并未被破坏，不必从置换档里读出来

W 此程序被交换到置换档的次数

c 此程序被强迫中断（像是分配到的 CPU 时间耗尽）的次数

w 此程序自愿中断（像是在等待某一个 I/O 执行完毕，像是磁碟读取等等）的次数

I 此程序所输入的档案数

O 此程序所输出的档案数

r 此程序所收到的 Socket Message

s 此程序所送出的 Socket Message

k 此程序所收到的信号 ( Signal )数量

4、Command Info

C 执行时的参数以及指令名称

x 指令的结束代码 ( Exit Status )

-p or --portability：这个选项会自动把显示格式设定成为：

real %e user %Usys %S：这么做的目的是为了与 POSIX 规格相容。

-v or --verbose：这个选项会把所有程序中用到的资源通通列出来，不但如一般英文语句，还有说明。对不想花时间去熟习格式设定或是刚刚开始接触这个指令的人相当有用。

### 实例

```
[root@localhost msbuild]# time date
Wed Dec 23 19:33:33 CST 2020

real	0m0.003s
user	0m0.000s
sys	    0m0.003s
```

在以上实例中，执行命令"time date"(见第1行)。

系统先执行命令"date"，第2行为命令"date"的执行结果。

第3-6行为执行命令"date"的时间统计结果，其中第4行"real"为实际时间，第5行"user"为用户CPU时间，第6行"sys"为系统CPU时间。

以上三种时间的显示格式均为MMmNN[.FFF]s。

* 测试程序耗时 test.c

```c
#include <stdio.h>
int main()
{
    FILE *fp = fopen("/tmp/testfile","w");
    int i=0;
    for(i=0;i<3000000;++i)
    {
    	fprintf(fp,"%d\n",i);
    }
    fclose(fp);
    return 0;
}

gcc test.c -o test
    
[root@localhost work]# time ./test

real	0m3.238s
user	0m2.868s
sys	    0m0.370s
```

* 测试 find 指令耗时
```
[root@localhost ~]# vim ~/.bash_profile ^C
[root@localhost ~]# time find / -name "hello"
/root/gcc-10.2.0/libgo/go/io/ioutil/testdata/hello
/root/gcc-10.2.0/libgo/go/cmd/go/testdata/src/vend/hello
/root/gcc-10.2.0/libgo/go/cmd/go/testdata/src/hello
/root/boost_1_74_0/tools/build/example/qt/qt4/hello
/root/boost_1_74_0/tools/build/example/qt/qt3/hello
/root/boost_1_74_0/tools/build/example/hello

real	0m23.690s
user	0m0.684s
sys	    0m1.506s

# 再次执行时间变短
[root@localhost ~]# time find / -name "hello"
/root/gcc-10.2.0/libgo/go/io/ioutil/testdata/hello
/root/gcc-10.2.0/libgo/go/cmd/go/testdata/src/vend/hello
/root/gcc-10.2.0/libgo/go/cmd/go/testdata/src/hello
/root/boost_1_74_0/tools/build/example/qt/qt4/hello
/root/boost_1_74_0/tools/build/example/qt/qt3/hello
/root/boost_1_74_0/tools/build/example/hello

real	0m0.738s
user	0m0.338s
sys	    0m0.400s

# 这个现象跟 Linux 操作系统的运行原理有关，
# find 命令在第一次执行后，系统会对一些文件做缓存，
# 在第二次执行时，就正好使用到了这些缓存中的数据，因此执行速度就变快了很多。
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)