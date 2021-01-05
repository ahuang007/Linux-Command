# Linux loadkeys 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux loadkeys 命令可以根据一个键盘定义表改变 linux 键盘驱动程序转译键盘输入过程。详细的说明请参考 dumpkeys。

### 语法

```
loadkeys [ -d --default ] [ -h --help ] [ -q --quiet ] [ -v --verbose [ -v --verbose ]...] [ -m --mktable ] [ -c --clearcompose ] [ -s --clearstrings ] [ filename... ]
```

**参数**:

- -v --verbose：印出详细的资料，你可以重复以增加详细度。
- -q --quiet：不要显示任何讯息。
- -c --clearcompose：清除所有 composite 定义。
- -s --clearstrings：将定串定义表清除。

### 实例

```
[root@localhost xmoba]# loadkeys
Loading <stdin>
string F80="hello"
//按下 Ctrl + D键 确定输入

[root@localhost xmoba]# dumpkeys --funcs-only //显示功能键
string F1 = "\033[[A"
string F2 = "\033[[B"
string F3 = "\033[[C"
string F4 = "\033[[D"
string F5 = "\033[[E"
string F6 = "\033[17~"
string F7 = "\033[18~"
string F8 = "\033[19~"
string F9 = "\033[20~"
string F10 = "\033[21~"
string F11 = "\033[23~"
string F12 = "\033[24~"
string F13 = "\033[25~"
string F14 = "\033[26~"
string F15 = "\033[28~"
string F16 = "\033[29~"
string F17 = "\033[31~"
string F18 = "\033[32~"
string F19 = "\033[33~"
string F20 = "\033[34~"
string Find = "\033[1~"
string Insert = "\033[2~"
string Remove = "\033[3~"
string Select = "\033[4~"
string Prior = "\033[5~"
string Next = "\033[6~"
string Macro = "\033[M"
string Pause = "\033[P"
string F80 = "hello"

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)