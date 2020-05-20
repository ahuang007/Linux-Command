# Linux lpr 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`lpr = Line PRint` 

lpr(line printer，按行打印)实用程序用来将一个或多个文件放入打印队列等待打印。

lpr 可以用来将料资送给本地或是远端的主机来处理。

### 语法

```
lpr [ -P printer ]
```

**参数**：

- -p Printer: 将资料送至指定的打印机 Printer，预设值为 lp。

### 实例

下面的命令行将在名为mailroom的打印机上打印report文件：

```
[root@localhost test ]$ lpr -P mailroom report 

# 由于缺少打印机 指令执行失败
lpr: The printer or class does not exist.
```

使用一条打印命令可打印多个文件，下面的命令行在名为laser1的打印机上打印3个文件：

```
[root@localhost test ]$ lpr -P laser1 1.txt 2.txt 3.txt 

# 由于缺少打印机 指令执行失败
lpr: The printer or class does not exist.
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)