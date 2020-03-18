# pidof 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

**pidof 命令**用于查找指定名称的进程的进程号 id 号。

### 语法 

```
pidof(选项)(参数)
```

### 选项 

```
-s：仅返回一个进程号；
-c：仅显示具有相同“root”目录的进程；
-x：显示由脚本开启的进程；
-o：指定不显示的进程ID。
```

### 参数 

进程名称：指定要查找的进程名称。

### 实例 

```
[dasheng.game@kfpub ~]$ pidof tmux
14894 13478
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)