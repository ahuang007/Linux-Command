# Linux find 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux find 命令用来在指定目录下查找文件。任何位于参数之前的字符串都将被视为欲查找的目录名。如果使用该命令时，不设置任何参数，则find命令将在当前目录下查找子目录与文件。并且将查找到的子目录和文件全部进行显示。

### 语法

```
find   path   -option   [   -print ]   [ -exec   -ok   command ]   {} \;
```

**参数说明** :

find 根据下列规则判断 path 和 expression，在命令列上第一个 - ( ) , ! 之前的部份为 path，之后的是 expression。如果 path 是空字串则使用目前路径，如果 expression 是空字串则使用 -print 为预设 expression。

expression 中可使用的选项有二三十个之多，在此只介绍最常用的部份。

-mount, -xdev : 只检查和指定目录在同一个文件系统下的文件，避免列出其它文件系统中的文件

-amin n : 在过去 n 分钟内被读取过

-anewer file : 比文件 file 更晚被读取过的文件

-atime n : 在过去n天内被读取过的文件

-cmin n : 在过去 n 分钟内被修改过

-cnewer file :比文件 file 更新的文件

-ctime n : 在过去n天内被修改过的文件

-empty : 空的文件-gid n or -group name : gid 是 n 或是 group 名称是 name

-ipath p, -path p : 路径名称符合 p 的文件，ipath 会忽略大小写

-name name, -iname name : 文件名称符合 name 的文件。iname 会忽略大小写

-size n : 文件大小 是 n 单位，b 代表 512 位元组的区块，c 表示字元数，k 表示 kilo bytes，w 是二个位元组。-type c : 文件类型是 c 的文件。

d: 目录

c: 字型装置文件

b: 区块装置文件

p: 具名贮列

f: 一般文件

l: 符号连结

s: socket

-pid n : process id 是 n 的文件

你可以使用 ( ) 将运算式分隔，并使用下列运算。

exp1 -and exp2

! expr

-not expr

exp1 -or exp2

exp1, exp2

### 实例

将目前目录及其子目录下所有延伸档名是 sh 的文件列出来。

```
[root@localhost trunk (dev ✗)]$ find . -name "*.sh"
./start.sh
./restart.sh
./gen_proto.sh
./run_config.sh
```

将目前目录其其下子目录中所有文件夹列出

```
[root@localhost trunk (dev ✗)]$ find ./bin -type d
./bin
./bin/runtime
./bin/runtime/center
./bin/runtime/center/log
./bin/runtime/fish_game
./bin/runtime/fish_game/log
```

将目前目录及其子目录下所有最近 1天内更新过的文件列出

```
[root@localhost trunk (dev ✗)]$ find bin -ctime 1
bin/runtime/center/log
bin/runtime/fish_game/log/ts_1__engine_file.log
bin/runtime/fish_game/log/rs_1__engine_file.log
bin/runtime/fish_game/log/fep_1__engine_file.log
bin/runtime/fish_game/log/ws_1__engine_file.log
bin/runtime/fish_game/log/agent_1__engine_file.log
```

查找/var/log目录中更改时间在7日以前的普通文件，并在删除之前询问它们：

```
[root@localhost trunk (dev ✗)]$ find /var/log -type f -mtime +7 -ok rm {} \;   
< rm ... /var/log/sa/sa15 > ? y
< rm ... /var/log/sa/sa20 > ? y
< rm ... /var/log/sa/sa24 > ? y
< rm ... /var/log/sa/sa17 > ? y
......
```

查找前目录中文件属主具有读、写权限，并且文件所属组的用户和其他用户具有读权限的文件：

```
[root@localhost trunk (dev ✗)]$ find . -type f -perm 755 -exec ls -l {} \;
-rwxr-xr-x. 1 root root 2085 Apr 18 15:20 ./start.sh
-rwxr-xr-x. 1 root root 2012 Apr 18 17:13 ./restart.sh
-rwxr-xr-x. 1 root root 107 Apr 24 17:26 ./gen_proto.sh
-rwxr-xr-x. 1 root root 1142 Apr 17 17:34 ./run_config.sh
-rwxr-xr-x. 1 root root 1602 Apr 17 17:34 ./start.bat
-rwxr-xr-x. 1 root root 766464 Apr 17 17:34 ./bin/lua5.3.0.dll
-rwxr-xr-x. 1 root root 8458240 Apr 17 17:34 ./bin/game_engine.exe
-rwxr-xr-x. 1 root root 1045128 Apr 17 17:34 ./bin/dbghelp.dll
-rwxr-xr-x. 1 root root 45501184 Apr 17 17:34 ./bin/game_engine

```

为了查找当前目录及其子目录所有文件长度为0的普通文件，并列出它们的完整路径：

```
[root@localhost trunk (dev ✗)]$ find . -type f -size 0 -exec ls -l {} \;
-rw-r--r--. 1 root root 0 Apr 17 17:34 ./center/dp/frame/database/mgr/frame_database_mgr_impl.lua
-rw-r--r--. 1 root root 0 Apr 17 17:34 ./center/dp/frame/database/mgr/frame_database_work_mgr.lua
-rw-r--r--. 1 root root 0 Apr 17 17:34 ./center/dp/frame/database/mgr/frame_database_back_mgr.lua
-rw-r--r--. 1 root root 0 Apr 17 17:34 ./center/dp/frame/database/mgr/frame_database_conn_idx_mgr.lua
-rw-r--r--. 1 root root 0 Mar 20 11:57 ./protocol/协议分段.txt
-rw-r--r--. 1 root root 0 Apr 28 21:02 ./bin/runtime/center/log/dp_1__engine_file.log
-rw-r--r--. 1 root root 0 Apr 28 21:02 ./bin/runtime/center/log/ts_1__engine_file.log
-rw-r--r--. 1 root root 0 Apr 28 21:02 ./bin/runtime/center/log/ls_1__engine_file.log
-rw-r--r--. 1 root root 0 Apr 28 21:02 ./bin/runtime/center/log/ss_1__engine_file.log
-rw-r--r--. 1 root root 0 Apr 28 21:02 ./bin/runtime/center/log/fep_1__engine_file.log
-rw-r--r--. 1 root root 0 Apr 28 21:02 ./bin/runtime/center/log/ws_1__engine_file.log
-rw-r--r--. 1 root root 0 Apr 28 21:02 ./bin/runtime/center/log/agent_1__engine_file.log
-rw-r--r--. 1 root root 0 May  6 20:55 ./bin/runtime/fish_game/log/ts_1__engine_file.log
-rw-r--r--. 1 root root 0 May  6 20:55 ./bin/runtime/fish_game/log/rs_1__engine_file.log
-rw-r--r--. 1 root root 0 May  6 20:55 ./bin/runtime/fish_game/log/fep_1__engine_file.log
-rw-r--r--. 1 root root 0 May  6 20:55 ./bin/runtime/fish_game/log/ws_1__engine_file.log
-rw-r--r--. 1 root root 0 May  6 20:55 ./bin/runtime/fish_game/log/agent_1__engine_file.log
```

查找代码中超过500k的lua文件

```
[root@localhost fish_game (dev ✗)]$ find ./script -type f -size +500k | grep lua
./script/trunk/public/game/fep/server/ip_area/ip_area_list.lua
./script/trunk/center/ss/server/ip_area/ip_area_list.lua
./script/trunk/center/ls/server/ip_area/ip_area_list.lua
./script/trunk/center/def/include/server/game/line_s.lua
./script/trunk/fish_game/def/include/server/game/line_s.lua
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)