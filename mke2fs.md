# Linux mke2fs 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux mke2fs 命令用于建立 ext2 文件系统。

### 语法

```
mke2fs [-cFMqrSvV][-b <区块大小>][-f <不连续区段大小>][-i <字节>][-N <inode数>][-l <文件>][-L <标签>][-m <百分比值>][-R=<区块数>][ 设备名称][区块数]
```

**参数**：

- -b<区块大小> 指定区块大小，单位为字节。
- -c 检查是否有损坏的区块。
- -f<不连续区段大小> 指定不连续区段的大小，单位为字节。
- -F 不管指定的设备为何，强制执行mke2fs。
- -i<字节> 指定"字节/inode"的比例。
- -N<inode数> 指定要建立的inode数目。
- -l<文件> 从指定的文件中，读取文件西中损坏区块的信息。
- -L<标签> 设置文件系统的标签名称。
- -m<百分比值> 指定给管理员保留区块的比例，预设为5%。
- -M 记录最后一次挂入的目录。
- -q 执行时不显示任何信息。
- -r 指定要建立的ext2文件系统版本。
- -R=<区块数> 设置磁盘阵列参数。
- -S 仅写入superblock与group descriptors，而不更改inode able inode bitmap以及block bitmap。
- -v 执行时显示详细信息。
- -V 显示版本信息。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)