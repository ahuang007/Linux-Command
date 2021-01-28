# Linux rdate命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux rdate命令用于显示其他主机的日期与时间。

执行rdate指令，向其他主机询问系统时间并显示出来。

### 语法

```
rdate [-ps][主机名称或IP地址...]
```

**参数**：

- -p 　显示远端主机的日期与时间。
- -s 　把从远端主机收到的日期和时间，回存到本地主机的系统时间。
- -u 传输协议使用UDP协议
- -l 使用syslog显示错误信息
- -t<时间> 设置超时时间

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)