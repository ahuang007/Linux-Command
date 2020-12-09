# Linux declare 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux declare 命令用于声明 shell 变量。

declare为 shell 指令，在第一种语法中可用来声明变量并设置变量的属性([rix]即为变量的属性），在第二种语法中可用来显示shell函数。若不加上任何参数，则会显示全部的shell变量与函数(与执行set指令的效果相同)。

### 语法

```
declare [+/-][rxi][变量名称＝设置值] 或 declare -f
```

**参数说明**：

- +/- 　"-"可用来指定变量的属性，"+"则是取消变量所设的属性。
- -f 　仅显示函数。
- r 　将变量设置为只读。
- x 　指定的变量会成为环境变量，可供shell以外的程序来使用。
- i 　[设置值]可以是数值，字符串或运算式。

### 实例

查看当前系统变量

```
[root@localhost ~]# declare
BASH=/bin/bash
BASHOPTS=checkwinsize:cmdhist:expand_aliases:extquote:force_fignore:histappend:hostcomplete:interactive_comments:login_shell:progcomp:promptvars:sourcepath
BASH_ALIASES=()
BASH_ARGC=()
BASH_ARGV=()
BASH_CMDS=()
BASH_LINENO=()
BASH_SOURCE=()
BASH_VERSINFO=([0]="4" [1]="2" [2]="46" [3]="2" [4]="release" [5]="x86_64-redhat-linux-gnu")
BASH_VERSION='4.2.46(2)-release'
COLUMNS=245
DIRSTACK=()
EUID=0
GROUPS=()
HISTCONTROL=ignoredups
HISTFILE=/root/.bash_history
HISTFILESIZE=1000
HISTSIZE=1000
HOME=/root
HOSTNAME=localhost.localdomain
HOSTTYPE=x86_64
ID=0
....
```

声明整数型变量

```
[root@localhost test]# cat test.sh 
declare -i ab
ab=56
echo $ab
[root@localhost test]# ./test.sh 
56
```

改变变量属性

```
[root@localhost test]# cat test1.sh 
declare -i ef
ef=1
echo "ef="$ef

ef="hello"
echo "ef="$ef

declare +i ef
ef="hello"
echo "ef="$ef
[root@localhost test]# ./test1.sh 
ef=1
ef=0
ef=hello
```

设置变量只读

```
declare -i ab
ab=56
echo $ab

declare -r ab
ab=88
echo $ab
[root@localhost test]# ./test.sh 
56
./test.sh: line 6: ab: readonly variable
56
```

声明数组变量

```
[root@localhost test]# cat test2.sh 
declare -a cd='([0]="a" [1]=“b” [2]="c")'
echo ${cd[1]}

echo ${cd[@]}
[root@localhost test]# ./test2.sh 
“b”
a “b” c
```

显示函数

```
[root@localhost test]# cat test3.sh 

add() 
{
	a=1
	b=2
	c=a+b
	echo $c
}

print() {
	echo "print"
}

declare -f

[root@localhost test]# ./test3.sh 
add () 
{ 
    a=1;
    b=2;
    c=a+b;
    echo $c
}
print () 
{ 
    echo "print"
}
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)