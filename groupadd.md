# Linux groupadd 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

groupadd 命令用于创建一个新的工作组，新工作组的信息将被添加到系统文件中。

相关文件:

- /etc/group 组账户信息。
- /etc/gshadow 安全组账户信息。
- /etc/login.defs Shadow密码套件配置。

### 语法

groupadd 命令 语法格式如下：

```
groupadd [-g gid [-o]] [-r] [-f] group
```

**参数说明：**

- -g：指定新建工作组的 id；
- -r：创建系统工作组，系统工作组的组ID小于 500；
- -K：覆盖配置文件 "/ect/login.defs"；
- -o：允许添加组 ID 号不唯一的工作组。
- -f,--force: 如果指定的组已经存在，此选项将失明了仅以成功状态退出。当与 -g 一起使用，并且指定的GID_MIN已经存在时，选择另一个唯一的GID（即-g关闭）。

### 实例

创建一个新的组，并添加组 ID。

```
[root@localhost ~]# groupadd -g 1001 test
```

此时在 /etc/group 文件中产生一个组 ID（GID）是 344 的项目。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)