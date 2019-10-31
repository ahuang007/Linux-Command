# Linux umask 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux umask 命令指定在建立文件时预设的权限掩码。

umask 可用来设定[权限掩码]。[权限掩码]是由3个八进制的数字所组成，将现有的存取权限减掉权限掩码后，即可产生建立文件时预设的权限。

### 语法

```
umask [-S][权限掩码]
```

**参数说明**：

-S 　以文字的方式来表示权限掩码。

### 实例

使用指令"umask"查看当前权限掩码，则输入下面的命令：

```
[huanglijun@localhost test1]$ umask  #获取当前权限掩码 
```

执行上面的指令后，输出信息如下：

```
0002
```

接下来，使用指令"mkdir"创建一个目录，并使用指令"ls"获取该目录的详细信息，输入命令如下：

```
$ mkdir test1                       #创建目录  
$ ls –d –l test1/                   #显示目录的详细信息  
```

执行上面的命令后，将显示新创建目录的详细信息，如下所示：

```
[huanglijun@localhost test]$ ls -d -l test1
drwxrwxr-x 2 huanglijun huanglijun 23 10月 10 09:54 test1
```

注意：在上面的输出信息中，"drwxrwxr-x"="777-0002=775"。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)