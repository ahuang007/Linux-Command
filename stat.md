# Linux stat 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux stat 命令用于显示 inode 内容。

stat 以文字的格式来显示 inode 的内容。

### 语法

```
stat [文件或目录]
```

### 实例

查看 testfile 文件的inode内容内容，可以用以下命令：

```
stat testfile
```

执行以上命令输出结果：

```
[root@localhost test ]$ stat testfile
  File: ‘testfile’
  Size: 46        	Blocks: 8          IO Block: 4096   regular file
Device: fd00h/64768d	Inode: 5547217     Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2020-08-03 10:58:15.770678822 +0800
Modify: 2020-08-03 10:58:15.772678939 +0800
Change: 2020-08-03 10:58:15.772678939 +0800
 Birth: -
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)