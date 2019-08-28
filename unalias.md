# Linux unalias 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

相反指令  [alias](https://github.com/ahuang007/Linux-Command/blob/master/alias.md)

Linux unalias 命令用于删除别名。

unalias 为 shell 内建指令，可删除别名设置。

### 语法

```
unalias [-a][别名]
```

**参数**：

- -a 　删除全部的别名。

### 实例

设置别名与删除别名

```
[huanglijun@localhost bin]$ alias lx=ls
[huanglijun@localhost bin]$ lx
text.txt
[huanglijun@localhost bin]$ unalias lx
[huanglijun@localhost bin]$ lx
bash: lx: 未找到命令...
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)