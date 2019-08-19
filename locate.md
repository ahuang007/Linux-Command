# Linux locate 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

locate 命令用来查找文件或目录。 

locate命令要比find -name快得多，原因在于它不搜索具体目录，而是搜索一个数据库 /var/lib/mlocate/mlocate.db 。这个数据库中含有本地所有文件信息。Linux系统自动创建这个数据库，并且每天自动更新一次，因此，我们在用 [whereis](https://github.com/ahuang007/Linux-Command/blob/master/whereis.md) 和 locate 查找文件时，有时会找到已经被删除的数据，或者刚刚建立文件，却无法查找到，原因就是因为数据库文件没有被更新。为了避免这种情况，可以在使用 locate 之前，先使用 [updatedb](https://github.com/ahuang007/Linux-Command/blob/master/updatedb.md) 命令，手动更新数据库。整个locate工作其实是由四部分组成的:

1. /usr/bin/updatedb    主要用来更新数据库，通过 [crontab](https://github.com/ahuang007/Linux-Command/blob/master/crontab.md) 自动完成的
2. /usr/bin/locate           查询文件位置
3. /etc/updatedb.conf   updatedb的配置文件
4. /var/lib/mlocate/mlocate.db  存放文件信息的文件

### 语法

```
locate [OPTION]... [PATTERN]...
```

**参数：**
```
-b, --basename         match only the base name of path names
-c, --count            只输出找到的数量
-d, --database DBPATH  使用DBPATH指定的数据库，而不是默认数据库 /var/lib/mlocate/mlocate.db
-e, --existing         only print entries for currently existing files
-L, --follow           follow trailing symbolic links when checking file existence (default)
-h, --help             显示帮助
-i, --ignore-case      忽略大小写
-l, --limit, -n LIMIT  limit output (or counting) to LIMIT entries
-m, --mmap             ignored, for backward compatibility
-P, --nofollow, -H     don't follow trailing symbolic links when checking file existence
-0, --null             separate entries with NUL on output
-S, --statistics       don't search for entries, print statistics about eachused database
-q, --quiet            安静模式，不会显示任何错误讯息
-r, --regexp REGEXP    使用基本正则表达式 
--regex            	   使用扩展正则表达式
-s, --stdio            ignored, for backward compatibility
-V, --version          显示版本信息
-w, --wholename        match whole path name (default)
```

### 实例

查找 [uname](https://github.com/ahuang007/Linux-Command/blob/master/uname.md) 文件，输入以下命令：

```
[huanglijun@localhost test]$ locate uname
/usr/bin/uname
/usr/libexec/openscap/probe_uname
/usr/share/man/man1/uname.1.gz
/usr/share/man/man1p/uname.1p.gz
/usr/share/man/man2/oldolduname.2.gz
/usr/share/man/man2/olduname.2.gz
/usr/share/man/man2/uname.2.gz
/usr/share/man/man3p/uname.3p.gz
/usr/share/man/zh_CN/man1/uname.1.gz
```

搜索 /usr/local/bin/ 目录下所有以 lua 开头的文件

```
[root@server ~ ]$ locate /usr/local/bin/lua
/usr/local/bin/lua
/usr/local/bin/lua53
/usr/local/bin/luac
/usr/local/bin/luac53
/usr/local/bin/luarocks
/usr/local/bin/luarocks-5.3
/usr/local/bin/luarocks-admin
/usr/local/bin/luarocks-admin-5.3
```

### 附加说明

locate 与 [find](https://github.com/ahuang007/Linux-Command/blob/master/find.md) 不同: find 是去硬盘找，locate 只在  /var/lib/mlocate 资料库中找。

locate 的速度比 [find](https://github.com/ahuang007/Linux-Command/blob/master/find.md) 快，它并不是真的查找，而是查数据库，一般文件数据库在 /var/lib/mlocate/mlocate.db 中，所以 locate 的查找并不是实时的，而是以数据库的更新为准，一般是系统自己维护，也可以手工升级数据库 ，看下面的示例：

```
[huanglijun@localhost test]$ touch new.txt
[huanglijun@localhost test]$ ls
new.txt  testfile_1  testfile_2  testfile_3  test.txt
[huanglijun@localhost test]$ locate new.txt
## 找不到文件
[huanglijun@localhost test]$ sudo updatedb
[huanglijun@localhost test]$ locate new.txt
/home/huanglijun/test/new.txt 
## updatedb后找到了
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)