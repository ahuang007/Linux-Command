# Linux tree 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

**注： tree不是Linux系统默认有的指令 需要安装 yum install -y tree**

Linux tree 命令用于以树状图列出目录的内容。

执行 tree 指令，它会列出指定目录下的所有文件，包括子目录里的文件。

### 语法

```
tree [-aACdDfFgilnNpqstux][-I <范本样式>][-P <范本样式>][目录...]
```

**参数说明**：

- -a 显示所有文件和目录。
- -A 使用ASNI绘图字符显示树状图而非以ASCII字符组合。
- -C 在文件和目录清单加上色彩，便于区分各种类型。
- -d 显示目录名称而非内容。
- -D 列出文件或目录的更改时间。
- -f 在每个文件或目录之前，显示完整的相对路径名称。
- -F 在执行文件，目录，Socket，符号连接，管道名称名称，各自加上"*","/","=","@","|"号。
- -g 列出文件或目录的所属群组名称，没有对应的名称时，则显示群组识别码。
- -i 不以阶梯状列出文件或目录名称。
- -I<范本样式> 不显示符合范本样式的文件或目录名称。
- -l 如遇到性质为符号连接的目录，直接列出该连接所指向的原始目录。
- -n 不在文件和目录清单加上色彩。
- -N 直接列出文件和目录名称，包括控制字符。
- -p 列出权限标示。
- -P<范本样式> 只显示符合范本样式的文件或目录名称。
- -q 用"?"号取代控制字符，列出文件和目录名称。
- -s 列出文件或目录大小。
- -t 用文件和目录的更改时间排序。
- -u 列出文件或目录的拥有者名称，没有对应的名称时，则显示用户识别码。
- -x 将范围局限在现行的文件系统中，若指定目录下的某些子目录，其存放于另一个文件系统上，则将该子目录予以排除在寻找范围外。

### 实例

以树状图列出当前目录结构。可直接使用如下命令：

```
[root@server test ]$ tree	#以树状图列出当前目录结构   
.							#当前目录结构  	
|-- c
|   |-- daemontest.c
|   |-- definetest.c
|   |-- floattest.c
|   |-- testc.c
|   |-- testglibc.c
|   `-- testmemcpy.c
|-- cpp
|   |-- a.out
|   |-- lambdatest.cpp
|   |-- mapTest.cpp
|   |-- msg.pb.cc
|   |-- msg.pb.h
|   |-- msg.proto
|   |-- mutabletest.cpp
|   |-- testproto.cpp
|   |-- threadtest.cpp
|   `-- vectorTest.cpp
|-- file1.txt
|-- lua
|   |-- PineappleAlgorithm.lua
|   |-- bit.lua
|   `-- test.lua
|-- py
|   |-- MySQL-python-1.2.3
|   |   |-- HISTORY
|   |   |-- MANIFEST.in
|   |   |-- MySQL_python.egg-info
|   |   |   |-- PKG-INFO
|   |   |   |-- SOURCES.txt
|   |   |   |-- dependency_links.txt
|   |   |   `-- top_level.txt
|   |   |-- MySQLdb
|   |   |   |-- __init__.py
|   |   |   |-- connections.py
|   |   |   |-- constants
|   |   |   |   |-- CLIENT.py
|   |   |   |   |-- CR.py
|   |   |   |   |-- ER.py
|   |   |   |   |-- FIELD_TYPE.py
|   |   |   |   |-- FLAG.py
|   |   |   |   |-- REFRESH.py
|   |   |   |   `-- __init__.py
|   |   |   |-- converters.py
|   |   |   |-- cursors.py
|   |   |   |-- release.py
|   |   |   `-- times.py
|   |   |-- PKG-INFO
|   |   |-- README
|   |   |-- _mysql.c
|   |   |-- _mysql_exceptions.py
|   |   |-- build
|   |   |   |-- lib.linux-x86_64-2.6
|   |   |   |   |-- MySQLdb
|   |   |   |   |   |-- __init__.py
|   |   |   |   |   |-- connections.py
|   |   |   |   |   |-- constants
|   |   |   |   |   |   |-- CLIENT.py
|   |   |   |   |   |   |-- CR.py
|   |   |   |   |   |   |-- ER.py
|   |   |   |   |   |   |-- FIELD_TYPE.py
|   |   |   |   |   |   |-- FLAG.py
|   |   |   |   |   |   |-- REFRESH.py
|   |   |   |   |   |   `-- __init__.py
|   |   |   |   |   |-- converters.py
|   |   |   |   |   |-- cursors.py
|   |   |   |   |   |-- release.py
|   |   |   |   |   `-- times.py
|   |   |   |   `-- _mysql_exceptions.py
|   |   |   `-- temp.linux-x86_64-2.6
|   |   |-- doc
|   |   |   |-- FAQ.txt
|   |   |   `-- MySQLdb.txt
|   |   |-- ez_setup.py
|   |   |-- metadata.cfg
|   |   |-- pymemcompat.h
|   |   |-- setup.cfg
|   |   |-- setup.py
|   |   |-- setup_common.py
|   |   |-- setup_common.pyc
|   |   |-- setup_posix.py
|   |   |-- setup_posix.pyc
|   |   |-- setup_windows.py
|   |   |-- site.cfg
|   |   `-- tests
|   |       |-- capabilities.py
|   |       |-- dbapi20.py
|   |       |-- test_MySQLdb_capabilities.py
|   |       |-- test_MySQLdb_dbapi20.py
|   |       `-- test_MySQLdb_nonstandard.py
|   |-- MySQL-python-1.2.3.tar.gz
|   `-- createdb.py
|-- sh
|   |-- a.txt
|   `-- clock.sh
|-- shm
|   |-- 1.c
|   |-- 2.c
|   |-- a.c
|   |-- a.out
|   |-- read
|   `-- write
|-- test_pb
|   |-- main.cpp
|   |-- test
|   |-- test.pb.cc
|   |-- test.pb.h
|   `-- test.proto
|-- tserver
|   |-- client.c
|   `-- server.c
`-- work
    |-- crypt
    |   |-- lcrypt.c
    |   |-- n.lua
    |   `-- rsa_test.lua
    `-- crypt.rar

21 directories, 96 files #统计信息，该目录共21个子目录，96个文件 
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)