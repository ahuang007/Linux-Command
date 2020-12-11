# Linux grpconv 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux grpconv(group convert to shadow password) 命令用于开启群组的投影密码。

Linux 系统里的用户和群组密码，分别存放在 /etc 目录下的 passwd 和 group 文件中。因系统运作所需，任何人都得以读取它们，造成安全上的破绽。投影密码将文件内的密码改存在 /etc 目录下的 shadow 和 gshadow 文件内，只允许系统管理者读取，同时把原密码置换为"x"字符。投影密码的功能可随时开启或关闭，您只需执行 grpconv 指令就能开启群组投影密码。

### 语法

```
grpconv
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)