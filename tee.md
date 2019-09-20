# Linux tee 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`tee = T(T形水管接口)`

Linux tee 命令用于读取标准输入的数据，并将其内容输出成文件。

tee 指令会从标准输入设备读取数据，将其内容输出到标准输出设备，同时保存成文件。

### 语法

```
tee [-ai][--help][--version][文件...]
```

**参数**：

- -a或--append 　附加到既有文件的后面，而非覆盖它．
- -i或--ignore-interrupts 　忽略中断信号。
- --help 　在线帮助。
- --version 　显示版本信息。

### 实例

使用指令 tee 将用户输入的数据同时保存到文件 file1 和 file2 中，输入如下命令：

```
[huanglijun@localhost test]$ tee file1 file2 #在两个文件中复制内容 

```

以上命令执行后，将提示用户输入需要保存到文件的数据，如下所示：

```
hello							#提示用户输入数据  
hello							#输出数据，进行输出反馈  
[huanglijun@localhost test]$ cat file1
hello
[huanglijun@localhost test]$ tee -a file1 file2 # 附加
world
world
[huanglijun@localhost test]$ cat file1
hello
world
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)