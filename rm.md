# Linux rm 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`rm = remove`

Linux rm 命令用于删除一个文件或者目录。

### 语法

```
rm [options] name...
```

**参数**：

- -i 删除前逐一询问确认。
- -f 即使原档案属性设为唯读，亦直接删除，无需逐一确认。
- -r 将目录及以下之档案亦逐一删除。

### 实例

删除文件可以直接使用rm命令，若删除目录则必须配合选项"-r"，例如：

```
# 询问
[huanglijun@localhost test]$ rm -i new.txt 
rm：是否删除普通空文件 "new.txt"？y

# 不询问
[huanglijun@localhost test]$ rm -f test.txt 

# 删除文件夹
[huanglijun@localhost test]$ rm -f d1
rm: 无法删除"d1": 是一个目录

[huanglijun@localhost test]$ rm -rf d1

```

删除当前目录下的所有文件及目录，命令行为：

```
rm  -rf  ./* 
```

文件一旦通过rm命令删除，则无法恢复，所以必须格外小心地使用该命令。

 **注意** 

```
#删除根目录
rm -rf / 

#为了避免误操作 不能随便给root权限

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)