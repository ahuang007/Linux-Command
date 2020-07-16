# Linux mzip 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux mzip 命令是 Zip/Jaz 磁盘驱动器控制指令。

mzip 为 [mtools](https://github.com/ahuang007/Linux-Command/blob/master/mtools.md) 工具指令，可设置 Zip 或 Jaz 磁盘驱动区的保护模式以及执行退出磁盘的动作。

### 语法

```
mzip [-efpqruwx]
```

**参数**：

- -e 退出磁盘。
- -f 与-e参数一并使用，不管是否已经挂入磁盘中的文件系统，一律强制退出磁盘。
- -p 设置磁盘的写入密码。
- -q 显示目前的状态。
- -r 将磁盘设为防写状态。
- -u 退出磁盘以前，暂时解除磁盘的保护状态。
- -w 将磁盘设为可写入状态。
- -x 设置磁盘的密码。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)