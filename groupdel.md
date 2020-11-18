# Linux groupdel 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux groupdel 命令用于删除群组。

需要从系统上删除群组时，可用 groupdel(group delete) 指令来完成这项工作。倘若该群组中仍包括某些用户，则必须先删除这些用户后，方能删除群组。

### 语法

```
groupdel [群组名称]
```

### 实例

删除一个群组

```
[root@localhost ~]# groupadd -g 1001 test
[root@localhost ~]# cat /etc/group | grep test
test:x:1001:
[root@localhost ~]# groupdel test
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)