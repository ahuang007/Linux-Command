# Linux tmpwatch 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux tmpwatch 命令用于删除暂存文件。

执行 tmpwatch 指令可删除不必要的暂存文件，您可以设置文件超期时间，单位以小时计算。

### 语法

```
tmpwatch [-afqv][--test][超期时间][目录...]
```

**参数**：

- -a或--all 　删除任何类型的文件。
- -f或--force 　强制删除文件或目录，其效果类似rm指令的"-f"参数。
- -q或--quiet 　不显示指令执行过程。
- -v或--verbose 　详细显示指令执行过程。
- -test 　仅作测试，并不真的删除文件或目录。

### 实例

使用指令"tmpwatch"删除目录"/tmp"中超过一天未使用的文件，输入如下命令：

```
root@server ~ ]$ tmpwatch 24 /tmp/ #删除/tmp目录中超过一天未使用的文件
```

注意：该指令需要 root 权限，因此在使用 tmpwatch 命令前应该使用 [su](https://github.com/ahuang007/Linux-Command/blob/master/su.md) 命令切换用户。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)