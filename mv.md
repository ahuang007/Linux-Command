# Linux mv 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

 `mv = move`

Linux mv 命令用来为文件或目录改名、或将文件或目录移入其它位置。

### 语法

```
mv [options] source dest
mv [options] source... directory
```

**参数说明**：

- -i: 若指定目录已有同名文件，则先询问是否覆盖旧文件;
- -f: 在mv操作要覆盖某已有的目标文件时不给任何指示;

mv参数设置与运行结果

| 命令格式         | 运行结果                                                     |
| :--------------- | :----------------------------------------------------------- |
| mv 文件名 文件名 | 将源文件名改为目标文件名                                     |
| mv 文件名 目录名 | 将文件移动到目标目录                                         |
| mv 目录名 目录名 | 目标目录已存在，将源目录 移动到目标目录；目标 目录不存在则改名 |
| mv 目录名 文件名 | 出错                                                         |

### 实例

将文件夹 A 更名为 文件夹 B :

将文件 testfile 更名为 testfile.bak

```
[huanglijun@localhost test]$ mv A B
[huanglijun@localhost test]$ mv testfile testfile.bak
```

将 d1 目录下的所有文件移动到当前目录下，命令行为：

```
[huanglijun@localhost test]$ mv d1/* .
```


返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)