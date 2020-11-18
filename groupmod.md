# Linux groupmod 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux groupmod 命令用于更改群组识别码或名称。

需要更改群组的识别码或名称时，可用 groupmod 指令来完成这项工作。

### 语法

```
groupmod [-g <群组识别码> <-o>][-n <新群组名称>][群组名称]
```

**参数**：

- -g <群组识别码> 　设置欲使用的群组识别码。
- -o 　重复使用群组识别码。
- -n <新群组名称> 　设置欲使用的群组名称。

### 实例

修改组名

```
[root@localhost ~]# groupadd -g 1001 test
[root@localhost ~]# cat /etc/group | grep test
test:x:1001:
[root@localhost ~]# groupmod -n test1 test
[root@localhost ~]# cat /etc/group | grep test
test1:x:1001:
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)