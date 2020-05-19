# Linux lprm 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux lprm 命令用于将一个工作由打印机贮列中移除

尚未完成的打印机工作会被放在打印机贮列之中，这个命令可用来将常未送到打印机的工作取消。由于每一个打印机都有一个独立的贮列，你可以用 -P 这个命令设定想要作用的印列机。如果没有设定的话，会使用系统预设的打印机。

　　这个命令会检查使用者是否有足够的权限删除指定的档案，一般而言，只有档案的拥有者或是系统管理员才有这个权限。

### 语法

```
lprm [P] [file...]
```

### 实例

将打印机 hpprinter 中的第 1123 号工作移除

```
[root@localhost test ]$ lprm -Phpprinter 1123

# 由于没有打印机 指令执行不了
lprm: Error - unknown destination "hpprinter".
```

将第 1011 号工作由预设印表机中移除

```
[root@localhost test ]$ lprm 1011

# 由于没有打印机 指令执行不了
lprm: Job #1011 does not exist.
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)