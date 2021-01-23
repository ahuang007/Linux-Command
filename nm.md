# Linux nm 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

nm是names的缩写， nm命令主要是用来列出某些文件中的符号（就是一些函数和全局变量等）。

### 语法格式

nm [参数]

**常用选项：**

| -A   | 每个符号前显示文件名 |
| ---- | -------------------- |
| -D   | 显示动态符号         |
| -g   | 仅显示外部符号       |
| -r   | 反序显示符号表       |

### 参考实例

显示hello.o 中的未定义符号，需要和其他对象文件进行链接：

```
[root@localhost work]# nm -u hello.o 
```

在/usr/lib/ 目录下找出哪个库文件定义了memset函数：

```
[root@localhost work]# nm -A /usr/lib/* 2>/dev/null | grep "T memset" 
```

显示nm的版本号：

```
[root@localhost work]# nm -v
```

显示调试符号：

```
[root@localhost work]# nm -a hello.o 
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)