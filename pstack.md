# Linux pstack 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

* pstack 命令可显示每个进程的栈跟踪。
* pstack 命令必须由相应进程的属主或 `root` 运行。
* 可以使用 pstack 来确定进程挂起的位置。此命令允许使用的唯一选项是要检查的进程的 `PID`。

## 实例

* pstree 以树状结构显示进程

  ```
  [root@mobasv ~]# pstree -p dev | grep GameServer
  GameServer(4052)-+-{GameServer}(4053)
                   |-{GameServer}(4055)
                   |-{GameServer}(4058)
                   |-{GameServer}(4059)
                   |-{GameServer}(4060)
                   |-{GameServer}(4061)
                   |-{GameServer}(4062)
                   |-{GameServer}(4063)
                   |-{GameServer}(4064)
                   |-{GameServer}(4065)
                   |-{GameServer}(4066)
                   |-{GameServer}(4067)
                   |-{GameServer}(4068)
                   |-{GameServer}(4069)
                   |-{GameServer}(4070)
                   |-{GameServer}(4071)
                   |-{GameServer}(4072)
                   |-{GameServer}(4073)
                   |-{GameServer}(4074)
                   |-{GameServer}(4075)
                   |-{GameServer}(4076)
                   |-{GameServer}(4077)
                   |-{GameServer}(4078)
                   |-{GameServer}(4079)
                   |-{GameServer}(4080)
                   |-{GameServer}(4081)
                   |-{GameServer}(4082)
                   |-{GameServer}(4083)
                   |-{GameServer}(4084)
                   |-{GameServer}(4085)
                   |-{GameServer}(4086)
                   |-{GameServer}(4087)
                   |-{GameServer}(4088)
                   |-{GameServer}(4089)
                   `-{GameServer}(4090)
  ```

  dev 为工作用户，-p 为显示进程识别码，GameServer 共启动了35个子线程，加上主线程共36个线程。

  ```
  [root@mobasv ~]# ps -LF 4052
  UID        PID  PPID   LWP  C NLWP    SZ   RSS PSR STIME TTY      STAT   TIME CMD
  dev       4052     1  4052  2   36 185884 13892  5 11:16 ?        Sl     1:12 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4053  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4055  0   36 185884 13892 11 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4058  0   36 185884 13892  3 11:16 ?        Sl     0:10 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4059  0   36 185884 13892  0 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4060  0   36 185884 13892 11 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4061  0   36 185884 13892 15 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4062  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4063  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4064  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4065  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4066  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4067  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4068  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4069  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4070  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4071  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4072  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4073  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4074  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4075  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4076  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4077  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4078  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4079  0   36 185884 13892  9 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4080  0   36 185884 13892  0 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4081  0   36 185884 13892 11 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4082  0   36 185884 13892  0 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4083  0   36 185884 13892  0 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4084  0   36 185884 13892  0 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4085  0   36 185884 13892 11 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4086  0   36 185884 13892  0 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4087  0   36 185884 13892 11 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4088  0   36 185884 13892  0 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4089  0   36 185884 13892 11 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  dev       4052     1  4090  0   36 185884 13892  0 11:16 ?        Sl     0:00 ./GameServer debug -d -c /data/xmoba//bin/config/template/GameServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  ```

  进程共启动了36个线程

* pstack显示每个进程的栈跟踪

  ```
  [root@mobasv ~]# pstack 4053
  Thread 1 (process 4053):
#0  0x00007fe841b7275d in read () from /lib64/libpthread.so.0
  #1  0x0000000000775e3c in ConsoleRedirection::loopSinkToFile (n32FileFd=0, strLogFolder=..., strModule=..., strServerName=..., strServerID=..., strServerHostID=..., siFileMaxSize=52428800) at /home/chenghuo/projects/supportlib/logger/src/ConsoleRedirection.cpp:77
  #2  0x0000000000777c19 in std::__invoke_impl<void, void (*)(int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, unsigned long), int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, unsigned long>(std::__invoke_other, void (*&&)(int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, unsigned long), int&&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >&&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >&&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >&&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >&&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >&&, unsigned long&&) (__f=@0x1eb3f98: 0x775d62 <ConsoleRedirection::loopSinkToFile(int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, unsigned long)>) at /usr/local/include/c++/10.2.0/bits/invoke.h:60
  #3  0x0000000000777a43 in std::__invoke<void (*)(int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, unsigned long), int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, unsigned long>(void (*&&)(int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, unsigned long), int&&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >&&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >&&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >&&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >&&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >&&, unsigned long&&) (__fn=@0x1eb3f98: 0x775d62 <ConsoleRedirection::loopSinkToFile(int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, unsigned long)>) at /usr/local/include/c++/10.2.0/bits/invoke.h:95
  #4  0x0000000000777858 in std::thread::_Invoker<std::tuple<void (*)(int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, unsigned long), int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, unsigned long> >::_M_invoke<0ul, 1ul, 2ul, 3ul, 4ul, 5ul, 6ul, 7ul> (this=0x1eb3ee8) at /usr/local/include/c++/10.2.0/thread:264
  #5  0x000000000077776c in std::thread::_Invoker<std::tuple<void (*)(int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, unsigned long), int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, unsigned long> >::operator() (this=0x1eb3ee8) at /usr/local/include/c++/10.2.0/thread:271
  #6  0x0000000000777750 in std::thread::_State_impl<std::thread::_Invoker<std::tuple<void (*)(int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, unsigned long), int, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >, unsigned long> > >::_M_run (this=0x1eb3ee0) at /usr/local/include/c++/10.2.0/thread:215
  #7  0x00007fe8413d0de0 in execute_native_thread_routine () at ../../../../../libstdc++-v3/src/c++11/thread.cc:80
  #8  0x00007fe841b6bea5 in start_thread () from /lib64/libpthread.so.0
  #9  0x00007fe840b1b96d in clone () from /lib64/libc.so.6
  ```
  

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)