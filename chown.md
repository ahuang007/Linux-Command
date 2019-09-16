# Linux chown 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`chown = change owner`

Linux/Unix 是多人多工操作系统，所有的文件皆有拥有者。利用 chown 将指定文件的拥有者改为指定的用户或组，用户可以是用户名或者用户ID；组可以是组名或者组ID；文件是以空格分开的要改变权限的文件列表，支持通配符。 。

一般来说，这个指令只有是由系统管理者(root)所使用，一般使用者没有权限可以改变别人的文件拥有者，也没有权限把自己的文件拥有者改设为别人。只有系统管理者(root)才有这样的权限。

**使用权限** : root

### 语法

```
chown [-cfhvR] [--help] [--version] user[:group] file...
```

**参数** :

- user : 新的文件拥有者的使用者 ID
- group : 新的文件拥有者的使用者组(group)
- -c : 显示更改的部分的信息
- -f : 忽略错误信息
- -h :修复符号链接
- -v : 显示详细的处理信息
- -R : 处理指定目录以及其子目录下的所有文件
- --help : 显示辅助说明
- --version : 显示版本

### 实例

将文件 file1.txt 的拥有者设为 root，群体的使用者 root:

```
[root@server test ]$ chown root:root file1.txt
[root@server test ]$ ll | grep file1 # 第三列为拥有者 第四列为群体的使用者
-rw-r--r--. 1 root root    0 Sep 16 10:37 file1.txt
```

将目前目录下的所有文件与子目录的拥有者皆设为 root，群体的使用者 root:

```
chown -R root:root *
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)