# Linux mkfs.minix 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux mkfs.minix 命令用于建立 Minix 文件系统。

mkfs.minix 可建立 Minix 文件系统。

### 语法

```
mkfs.minix [-cv][-i <inode数目>][-l <文件>][-n <文件名长度>][设备名称][区块数]
```

**参数**：

- -c 检查是否有损坏的区块。
- -i<inode数目> 指定文件系统的inode总数。
- -l<文件> 从指定的文件中，读取文件系统中损坏区块的信息。
- -n<文件名长度> 指定文件名称长度的上限。
- -v 建立第2版的Minix文件系统。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)