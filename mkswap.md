# Linux mkswap 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux mkswap 命令用于设置交换区(swap area)。

mkswap 可将磁盘分区或文件设为 Linux 的交换区。

### 语法

```
mkswap [-cf][-v0][-v1][设备名称或文件][交换区大小]
```

**参数**：

- -c 建立交换区前，先检查是否有损坏的区块。
- -f 在SPARC电脑上建立交换区时，要加上此参数。
- -v0 建立旧式交换区，此为预设值。
- -v1 建立新式交换区。
- [交换区大小] 指定交换区的大小，单位为1024字节。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)