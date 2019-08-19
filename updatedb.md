# Linux updatedb 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

updatedb 创建或更新 mlocate 数据库
### 功能描述：

　　使用 updatedb 命令可以创建或更新 [locate](https://github.com/ahuang007/Linux-Command/blob/master/locate.md) 所使用的数据库。如果数据库已经存在，它的数据是重复使用，以避免重读并没有改变的目录。updatedb 通常每天由 [crontab](https://github.com/ahuang007/Linux-Command/blob/master/crontab.md) 运行来更新默认的数据库。

#### 命令语法：

　　updatedb [选项]

#### updatedb命令选项含义

| 选项                      | 含义                                                         |
| ------------------------- | ------------------------------------------------------------ |
| -n<名称>                  | 在空格分隔的列表名称中添加条目到PRUENAMES                    |
| -c<路径>                  | 在空格分隔的列表路径中添加条目到PRUNEPATHS                   |
| -U<路径>                  | 只存储扫描指定路径生成的数据库。默认扫描整个文件系统         |
| --debug-pruning           | 写入有关pruning decisions调试信息到标准错误输出              |
| --prune-bind-mounts<标志> | 设置PRUNE_BIND_MOUNTS标志，覆盖配置文件                      |
| -f<文件系统>              | 在空格分隔的列表文件系统中添加条目到PRUNEFS                  |
| -o<文件>                  | 写入数据库到指定文件，而不是使用默认的数据库                 |
| -v                        | 输出文件的路径名到标准输出                                   |
| -prunefs<文件系统>        | 设置PRUNEFS为指定文件系统，覆盖配置文件                      |
| -l<标记>                  | 在生成数据库到指定标记中，设置“require file visibility before reporting it”标记 |
| --prunenames<名称>        | 设置PRUNENAMES为指定名称，覆盖配置文件                       |
| --prunepaths<路径>        | 设置PRUNEPATHS为指定路径，覆盖配置文件                       |

* 例如：更新 mlocate 数据库

```
[huanglijun@localhost test]$ touch new.txt
[huanglijun@localhost test]$ ls
new.txt  testfile_1  testfile_2  testfile_3  test.txt
[huanglijun@localhost test]$ locate new.txt
## 找不到文件
[huanglijun@localhost test]$ sudo updatedb
[huanglijun@localhost test]$ locate new.txt
/home/huanglijun/test/new.txt 
## updatedb后找到了
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)