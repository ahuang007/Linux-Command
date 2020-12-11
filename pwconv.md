# Linux pwconv 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux pwconv 命令用于开启用户的投影密码。

Linux 系统里的用户和群组密码，分别存放在名称为 passwd 和 group 的文件中，　这两个文件位于 /etc 目录下。因系统运作所需，任何人都得以读取它们，造成安全上的破绽。投影密码将文件内的密码改存在 /etc 目录下的 shadow 和 gshadow 文件内，只允许系统管理者读取，同时把原密码置换为"x"字符，有效的强化了系统的安全性。

### 语法

```
pwconv
```

### 实例

开启用户的投影密码

```
[root@localhost ~]# pwconv
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)