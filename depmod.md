# Linux depmod 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`depmod = depend module`

Linux depmod 命令用于分析可载入模块的相依性。

depmod 可检测模块的相依性，供 [modprobe](https://github.com/ahuang007/Linux-Command/blob/master/modprobe.md) 在安装模块时使用。

### 语法

```
depmod [-adeisvV][-m <文件>][--help][模块名称]
```

**参数说明**：

- -a或--all 　分析所有可用的模块。
- -d或debug 　执行排错模式。
- -e 　输出无法参照的符号。
- -i 　不检查符号表的版本。
- -m<文件>或system-map<文件> 　使用指定的符号表文件。
- -s或--system-log 　在系统记录中记录错误。
- -v或--verbose 　执行时显示详细的信息。
- -V或--version 　显示版本信息。
- --help 　显示帮助。

### 实例

显示可用模块

```
[root@server modules ]$ depmod -a
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)