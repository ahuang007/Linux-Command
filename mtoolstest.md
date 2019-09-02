# Linux mtoolstest 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux mtoolstest 命令用于测试并显示 [mtools](https://github.com/ahuang007/Linux-Command/blob/master/mtools.md) 的相关设置。

mtoolstest 为 mtools 工具指令，可读取与分析 mtools 的配置文件，并在屏幕上显示结果。

### 语法

```
mtoolstest
```

### 实例

在命令行中直接输入 mtoolstest，即可显示 mtools 软件包当前的配置信息，结果如下：

```
[app@localhost service]$ mtoolstest
drive J:
	#fn=0 mode=0 builtin
	file="/dev/sdb4" fat_bits=16 
	tracks=0 heads=0 sectors=0 hidden=0
	offset=0x0
	partition=0
	mformat_only 

drive Z:
	#fn=0 mode=0 builtin
	file="/dev/sdb4" fat_bits=16 
	tracks=0 heads=0 sectors=0 hidden=0
	offset=0x0
	partition=0
	mformat_only 

drive X:
	#fn=0 mode=0 builtin
	file="$DISPLAY" fat_bits=0 
	tracks=0 heads=0 sectors=0 hidden=0
	offset=0x0
	partition=0
	

drive A:
	#fn=2 mode=128 defined in /etc/mtools.conf
	file="/dev/fd0" fat_bits=0 
	tracks=0 heads=0 sectors=0 hidden=0
	offset=0x0
	partition=0
	mformat_only 
	exclusive 

drive B:
	#fn=2 mode=128 defined in /etc/mtools.conf
	file="/dev/fd1" fat_bits=0 
	tracks=0 heads=0 sectors=0 hidden=0
	offset=0x0
	partition=0
	mformat_only 
	exclusive 

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)