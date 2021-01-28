# Linux fsck.minix 命令

Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux fsck.minix 命令用于检查文件系统并尝试修复错误。

当 minix 文件系统发生错误时，可用 fsck.minix 指令尝试加以参考。

### 语法

```
fsck.minix [-aflmrsv][外围设备代号]
```

**参数**：

- -a 自动修复文件系统，不询问任何问题。
- -f 强制对该文件系统进行完整检查，纵然该文件系统在慨略检查下没有问题。
- -l 列出所有文件名称。
- -m 使用类似MINIX操作系统的警告信息。
- -r 采用互动模式，在执行修复时询问问题，让用户得以确认并决定处理方式。
- -s 显示该分区第一个磁区的相关信息。
- -v 显示指令执行过程。

Linux 命令大全](https://ahuang007.github.com/Linux-Command)