# Linux suspend 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux suspend 命令用于暂停执行 shell。

suspend 为 shell 内建指令，可暂停目前正在执行的 shell。若要恢复，则必须使用 SIGCONT 信息。

### 语法

```
suspend [-f]
```

**参数说明**：

- -f 　若目前执行的 shell 为登入的 shell，则 suspend 预设无法暂停此 shell。若要强迫暂停登入的 shell，则必须使用 -f 参数。

### 实例

暂停shell

```
[jump@cocosfish log]$ suspend 
-bash: suspend: cannot suspend a login shell
[jump@cocosfish log]$ suspend -f

# 此时 在当前终端无法做其他事情 再开一个终端 执行下面这条指令当前终端才退出

[jump@cocosfish ~]$ killall -SIGCONT bash

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)