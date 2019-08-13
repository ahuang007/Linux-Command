# Linux cut 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux cut 命令用于显示每行从开头算起 num1 到 num2 的文字。

### 语法

```
cut  [-bn] [file]
cut [-c] [file]
cut [-df] [file]
```

**使用说明:**

cut 命令从文件的每一行剪切字节、字符和字段并将这些字节、字符和字段写至标准输出。

如果不指定 File 参数，cut 命令将读取标准输入。必须指定 -b、-c 或 -f 标志之一。

**参数:**

- -b ：以字节为单位进行分割。这些字节位置将忽略多字节字符边界，除非也指定了 -n 标志。
- -c ：以字符为单位进行分割。
- -d ：自定义分隔符，默认为制表符。
- -f ：与-d一起使用，指定显示哪个区域。
- -n ：取消分割多字节字符。仅和 -b 标志一起使用。如果字符的最后一个字节落在由 -b 标志的 List 参数指示的
  范围之内，该字符将被写出；否则，该字符将被排除

### 实例

当你执行 [who](https://github.com/ahuang007/Linux-Command/blob/master/cksum.md) 命令时，会输出类似如下的内容：

```
[root@server StressTest ]$ who
root     tty1         Aug 13 09:46 (:0)
root     pts/0        Aug 13 09:53 (192.168.11.72)
root     pts/1        Aug 13 09:54 (192.168.11.72)
```

如果我们想提取每一行的第1个字节，就这样：

```
[root@server StressTest ]$ who | cut -b 1     
r
r
r
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)