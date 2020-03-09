# Linux sync 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux sync 命令用于数据同步,sync 命令是在关闭 Linux 系统时使用的。

Linux 系统中欲写入硬盘的资料有的时候会了效率起见，会写到 filesystem buffer 中，这个 buffer 是一块记忆体空间，如果欲写入硬盘的资料存于此 buffer 中，而系统又突然断电的话，那么资料就会流失了，sync 指令会将存于 buffer 中的资料强制写入硬盘中。

### 语法

```
sync
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)