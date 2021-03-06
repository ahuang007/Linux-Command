# Linux mdir 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux mdir 命令用于显示 MS-DOS 目录。

mdir 为 [mtools](https://github.com/ahuang007/Linux-Command/blob/master/mtools.md) 工具指令，模拟 MS-DOS 的 dir 指令，可显示 MS-DOS 文件系统中的目录内容。

### 语法

```
mdir [-afwx/][目录]
```

**参数**：

- -/ 显示目录下所有子目录与文件。
- -a 　显示隐藏文件。
- -f 　不显示磁盘所剩余的可用空间。
- -w 　仅显示目录或文件名称，并以横排方式呈现，以便一次能显示较多的目录或文件。
- -X 　仅显示目录下所有子目录与文件的完整路径，不显示其他信息。

### 实例

显示a盘中的内容

```
$ mdir -/ a:\*   
```

以上命令执行后，mdir将显示指定盘"a:\"中的所有子目录及其中的文件信息，如下所示：

```
Volume in drive A has no label  #加载信息  
Volume Serial Number is 13D2~055C  
Directory for A:\                   #以下为目录信息  
./TEST <DIR> 2011-08-23 16:59     
#显示格式为文件名，目录大小，修改时间  
AUTORUN.INF 265 2011-08-23 16:53  
AUTORUN.BAT 43 2011-08-23 16:56  
3 files 308 bytes               #统计总大小  
724 325 bytes free              #剩余空间  
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)