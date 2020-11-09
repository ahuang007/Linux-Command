# Linux httpd 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux httpd 命令是 Apache HTTP 服务器程序。

httpd 为 Apache HTTP 服务器程序。直接执行程序可启动服务器的服务。

### 语法

```
httpd [-hlLStvVX][-c<httpd指令>][-C<httpd指令>][-d<服务器根目录>][-D<设定文件参数>][-f<设定文件>]
```

**参数说明**：

- -c<httpd指令> 在读取配置文件前，先执行选项中的指令。
- -C<httpd指令> 在读取配置文件后，再执行选项中的指令。
- -d<服务器根目录> 指定服务器的根目录。
- -D<设定文件参数> 指定要传入配置文件的参数。
- -f<设定文件> 指定配置文件。
- -h 显示帮助。
- -l 显示服务器编译时所包含的模块。
- -L 显示httpd指令的说明。
- -S 显示配置文件中的设定。
- -t 测试配置文件的语法是否正确。
- -v 显示版本信息。
- -V 显示版本信息以及建立环境。
- -X 以单一程序的方式来启动服务器。

### 实例

检查配置文件语法错误

```
[root@iZwz9i5ym7nzoefwpmoszjZ ~]# httpd -t
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.18.106.167. Set the 'ServerName' directive globally to suppress this message
Syntax OK
```

启动httpd

```
[root@iZwz9i5ym7nzoefwpmoszjZ ~]# httpd
AH00558: httpd: Could not reliably determine the server's fully qualified domain name, using 172.18.106.167. Set the 'ServerName' directive globally to suppress this message
(98)Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
AH00015: Unable to open logs
```

显示编译模块

```
[root@iZwz9i5ym7nzoefwpmoszjZ ~]# httpd -l
Compiled in modules:
  core.c
  mod_so.c
  http_core.c
```

显示配置文件

```
[root@iZwz9i5ym7nzoefwpmoszjZ ~]# httpd -L
<Directory (core.c)
        Container for directives affecting resources located in the specified directories
        Allowed in *.conf only outside <Directory>, <Files>, <Location>, or <If>
<Location (core.c)
        Container for directives affecting resources accessed through the specified URL paths
        Allowed in *.conf only outside <Directory>, <Files>, <Location>, or <If>
<VirtualHost (core.c)
        Container to map directives to a particular virtual host, takes one or more host addresses
        Allowed in *.conf only outside <Directory>, <Files>, <Location>, or <If>
<Files (core.c)
        Container for directives affecting files matching specified patterns
        Allowed in *.conf anywhere and in .htaccess
        when AllowOverride isn't None
<Limit (core.c)
        Container for authentication directives when accessed using specified HTTP methods
        Allowed in *.conf only inside <Directory>, <Files>, <Location>, or <If> and in .htaccess
        when AllowOverride includes AuthConfig or Limit
......

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)