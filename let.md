# Linux let 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

## 命令：let

let 命令是 BASH 中用于计算的工具，用于执行一个或多个表达式，变量计算中不需要加上 $ 来表示变量。如果表达式中包含了空格或其他特殊字符，则必须引起来。

### 语法格式

```
let arg [arg ...]
```

### 参数说明：

arg：要执行的表达式

### 实例：

自加操作：**let no++**

自减操作：**let no--**

简写形式 **let no+=10，let no-=20**，分别等同于 **let no=no+10，let no=no-20**。

以下实例计算 a 和 b 两个表达式，并输出结果：

```
[huanglijun@localhost project]$ let a=5+4; let b=9-3; echo $a $b
9 6
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)