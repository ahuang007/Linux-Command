# Linux expr 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

expr 命令是一个手工命令行计数器，用于在 UNIX/LINUX 下求表达式变量的值，一般用于整数值，也可用于字符串。

### 语法

```
expr 表达式
```

**表达式说明:**

- 用空格隔开每个项；
- 用 / (反斜杠) 放在 shell 特定的字符前面；
- 对包含空格和其他特殊字符的字符串要用引号括起来

### 实例

1、计算字串长度

```
[root@localhost test ]$ expr length "hello world"
11
```

2、抓取字串

```
[root@localhost test ]$ expr substr "hello world" 4 5
lo wo
```

3、抓取第一个字符数字串出现的位置

```
[root@localhost test ]$ expr index "hello world" w
7
```

4、整数运算

```
[root@localhost test ]$ expr 14 % 9
5

[root@localhost test ]$ expr 10 + 10
20

[root@localhost test ]$ expr 30 / 3 / 2
5

#(使用乘号时，必须用反斜线屏蔽其特定含义。因为shell可能会误解显示星号的意义)
[root@localhost test ]$ expr 30 * 3
expr: syntax error

[root@localhost test ]$ expr 30 \* 3
90
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)