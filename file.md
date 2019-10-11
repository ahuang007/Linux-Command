# Linux file 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux file 命令用于辨识文件类型。

通过 file 指令，我们得以辨识该文件的类型。

### 语法

```
file [-bcLvz][-f <名称文件>][-m <魔法数字文件>...][文件或目录...]
```

**参数**：

- -b 　列出辨识结果时，不显示文件名称。
- -c 　详细显示指令执行过程，便于排错或分析程序执行的情形。
- -f<名称文件> 　指定名称文件，其内容有一个或多个文件名称时，让 file 依序辨识这些文件，格式为每列一个文件名称。
- -L 　直接显示符号连接所指向的文件的类别。
- -m<魔法数字文件> 　指定魔法数字文件。
- -v 　显示版本信息。
- -z 　尝试去解读压缩文件的内容。
- [文件或目录...] 要确定类型的文件列表，多个文件之间使用空格分开，可以使用shell通配符匹配多个文件。

### 实例

显示文件类型：

```
[app@localhost texas_poker_game_2d_gold_formal_1]$ file texasPokerGame.log 
texasPokerGame.log: UTF-8 Unicode text

#不显示文件名
[app@localhost texas_poker_game_2d_gold_formal_1]$ file -b texasPokerGame.log 
UTF-8 Unicode text

# 显示MIME类别
[app@localhost texas_poker_game_2d_gold_formal_1]$ file -i texasPokerGame.log 
texasPokerGame.log: text/plain; charset=utf-8

[root@localhost ~]# file -b -i install.log
text/plain; charset=utf-8

# 软连接
[huanglijun@localhost test]$ ll | grep file1.slnk 
lrwxrwxrwx 1 huanglijun huanglijun  5 9月  25 10:02 file1.slnk -> file1

[huanglijun@localhost test]$ file file1.slnk 
file1.slnk: symbolic link to `file1'

# 文件夹
[huanglijun@localhost test]$ file -L test1
test1: directory

# shell文件
[app@localhost texas_poker_game_2d_gold_formal_1]$ file start.sh 
start.sh: a /usr/bin/env bash script, ASCII text executable

# 可执行文件
[app@localhost texas_poker_game_2d_gold_formal_1]$ file texasPokerGame
texasPokerGame: ELF 64-bit LSB executable, x86-64, version 1 (GNU/Linux), dynamically linked (uses shared libs), for GNU/Linux 2.6.32, BuildID[sha1]=25eef54997a110dbc542851972f2eec6bf99fd08, not stripped

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)