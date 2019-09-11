# Linux mktemp 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`mktemp = make temporary file`

Linux mktemp 命令用于建立暂存文件。

mktemp 建立的一个暂存文件，供 shell script 使用。

### 语法

```
mktemp [-qu][文件名参数]
```

**参数**：

- -q 　执行时若发生错误，不会显示任何信息。
- -u 　暂存文件会在mktemp结束前先行删除。
- [文件名参数] 　文件名参数必须是以"自订名称.XXXXXX"的格式。

### 实例

使用 mktemp 命令生成临时文件时，文件名参数应当以"文件名.XXXX"的形式给出，mktemp 会根据文件名参数建立一个临时文件。在命令行提示符输入如下命令：

```
[huanglijun@localhost test]$ mktemp tmp.xxxx
mktemp: 模板"tmp.xxxx" 中X 太少
[huanglijun@localhost test]$ mktemp tmp.XXXX #大写
tmp.aKFu
[huanglijun@localhost test]$ ls
boot.txt.bak  testfile_1  testfile_1_bak  testfile_2  testfile_3  tmp.aKFu

```

由此可见，生成的临时文件为tmp.akFu，其中，文件名参数中的"XXXX"被4 个随机产生的字符所取代。

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)