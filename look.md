# Linux look 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux look 命令用于查询单词。

look 指令用于英文单字的查询。您仅需给予它欲查询的字首字符串，它会显示所有开头字符串符合该条件的单字。

### 语法

```
look [-adf][-t<字尾字符串>][字首字符串][字典文件]
```

**参数说明**：

- -a 使用另一个字典文件web2，该文件也位于/usr/dict目录下。
- -d 只对比英文字母和数字，其余一慨忽略不予比对。
- -f 忽略字符大小写差别。
- -t<字尾字符串> 设置字尾字符串。

### 实例

原文件testfile中的内容如下：

```
[huanglijun@localhost test]$ cat testfile_1

Hello 95
Linux 85
test 30i

```

在testfile文件中使用look命令查找以"L"开头的单词，结果如下：

```
$ look L testfile_1                        		#查找以“L”开头的单词  
Linux 85                                    	#第四行以“L”开头，列出全句 
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)