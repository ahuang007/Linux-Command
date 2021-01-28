# Linux smbd 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux smbd 命令用于 Samba 服务器程序。

smbd 为 Samba 服务器程序，可分享文件与打印机等网络资源供 Windows 相关的用户端程序存取。

### 语法

```
smbd [-aDhoP][-d<排错层级>][-i<范围>][-l<记录文件>][-O<连接槽选项>][-p<连接端口编号>][-s<配置文件>]
```

**参数说明**：

- -a 所有的连线记录都会加到记录文件中。
- -d<排错层级> 指定记录文件所记载事件的详细程度。
- -D 使用此参数时，smbd会以服务程序的方式在后台执行。
- -h 显示帮助。
- -i<范围> 指定NetBIOS名称的范围。
- -l<记录文件> 指定记录文件的名称。
- -o 每次启动时，会覆盖原有的记录文件。
- -O<连接槽选项> 设置连接槽选项。
- -p<连接端口编号> 设置连接端口编号。
- -P 仅用来测试smbd程序的正确性。
- -s<配置文件> 指定smbd的设置文件。

### 实例

启动Samba服务器

```
# smbd -D
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)