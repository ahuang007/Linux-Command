# Linux quota 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux quota 命令用于显示磁盘已使用的空间与限制。

执行 quota 指令，可查询磁盘空间的限制，并得知已使用多少空间。

### 语法

```
quota [-quvV][用户名称...] 或 quota [-gqvV][群组名称...]
```

**参数说明**：

- -g 列出群组的磁盘空间限制。
- -q 简明列表，只列出超过限制的部分。
- -u 列出用户的磁盘空间限制。
- -v 显示该用户或群组，在所有挂入系统的存储设备的空间限制。
- -V 显示版本信息。

### 实例

```
# quota -guvs    <==显示目前执行者（就是 root ）的 quota 值 
# quota -uvs test <==显示 test 这个使用者的 quota 值
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)