# Linux newgrp 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux newgrp 命令用于登入另一个群组。

`newgrp = new group`

newgrp 指令类似 [login](https://github.com/ahuang007/Linux-Command/blob/master/login.md) 指令，当它是以相同的帐号，另一个群组名称，再次登入系统。

欲使用 newgrp 指令切换群组，您必须是该群组的用户，否则将无法登入指定的群组。

单一用户要同时隶属多个群组，需利用交替用户的设置。

若不指定群组名称，则 newgrp 指令会登入该用户名称的预设群组。

### 语法

```
newgrp [群组名称]
```

### 实例

改变群组

```
[root@localhost work]# newgrp root
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)