# Linux egrep 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux egrep 命令用于在文件内查找指定的字符串。

egrep 执行效果与"grep-E"相似，使用的语法及参数可参照grep指令，与grep的不同点在于解读字符串的方法。

egrep 是用extended regular expression语法来解读的，而grep则用basic regular expression 语法解读，extended regular expression比basic regular expression的表达更规范。

### 语法

```
egrep [范本模式] [文件或目录] 
```

**参数说明：**

- [范本模式] ：查找的字符串规则。
- [文件或目录] ：查找的目标文件或目录。

### 实例

显示文件中符合条件的字符。例如，查找当前目录下所有文件中包含字符串"read"的文件，可以使用如下命令：

```
[huanglijun@localhost read]$ egrep read ./*
./test1.sh:read num 
./test2.sh:if read -t 5 -p "输入一个数：" num
./test3.sh:read -n1 -p "Do you want to continue [Y/N]?" answer
./test4.sh:read -n2 -p "请随便输入两个字符: " any
./test5.sh:read  -s  -p "请输入您的密码:" pass
./test6.sh:cat test.txt | while read line      # cat 命令的输出作为read命令的输入,read读到>的值放在line中
./test.sh:read num 
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)