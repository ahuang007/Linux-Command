# Linux chroot 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux chroot 命令用于改变根目录。

`chroot = change root`

chroot 命令把根目录换成指定的目的目录。

### 语法

```
chroot [--help][--version][目的目录][执行指令...]
```

**参数说明**：

- --help 　在线帮助。
- --version 　显示版本信息。

### 实例

改变根目录

```
[root@server test ]$ chroot /mnt
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)