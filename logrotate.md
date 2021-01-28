# Linux logrotate 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux logrotate 命令用于管理记录文件。

使用 logrotate 指令，可让你轻松管理系统所产生的记录文件。它提供自动替换，压缩，删除和邮寄记录文件，每个记录文件都可被设置成每日，每周或每月处理，也能在文件太大时立即处理。您必须自行编辑，指定配置文件，预设的配置文件存放在/etc目录下，文件名称为 logrotate.conf。

### 语法

```
logrotate [-?dfv][-s <状态文件>][--usage][配置文件]
```

**参数说明**：

- -?或--help 　在线帮助。
- -d或--debug 　详细显示指令执行过程，便于排错或了解程序执行的情况。
- -f或--force 　强行启动记录文件维护操作，纵使logrotate指令认为没有需要亦然。
- -s<状态文件>或--state=<状态文件> 　使用指定的状态文件。
- -v或--version 　显示指令执行过程。
- --usage 　显示指令基本用法。

### 实例

指定记录文件

```
[root@localhost xmoba]# logrotate /root/config.log
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)