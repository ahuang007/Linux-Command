# Linux nl 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`nl = number of lines`

nl命令用于计算文件中行号。nl可以将输出的内容自动加上行号，其可以将行号做比较多的显示设计，包括位数和是否自动补0等等的功能。

### 1．命令格式：

```
nl [选项] [文件]
```

### 2．命令参数：

-b ：指定行号指定的方式，主要有两种：

-b a ：表示不论是否为空行，也同样列出行号(类似 cat -n)；

-b t ：如果有空行，空的那一行不要列出行号(默认值)；

-n ：列出行号表示的方法，主要有三种：

-n ln ：行号在萤幕的最左方显示；

-n rn ：行号在自己栏位的最右方显示，且不加 0 ；

-n rz ：行号在自己栏位的最右方显示，且加 0 ；

-w ：行号栏位的占用的位数。

-p 在逻辑定界符处不重新开始计算。 

### 3．命令功能：

nl 命令读取 File 参数（缺省情况下标准输入），计算输入中的行号，将计算过的行号写入标准输出。 在输出中，nl 命令根据您在命令行中指定的标志来计算左边的行。 输入文本必须写在逻辑页中。每个逻辑页有头、主体和页脚节（可以有空节）。 除非使用 -p 标志，nl 命令在每个逻辑页开始的地方重新设置行号。 可以单独为头、主体和页脚节设置行计算标志（例如，头和页脚行可以被计算然而文本行不能）。

### 4．使用实例：

* 实例一：用 nl 列出 test1.c 的内容

```
[root@localhost test]# nl test1.c
     1	#include <stdio.h>
     2	#include <stddef.h>
       
     3	int main() {
     4		printf("sizeof(wchar_t): %d\n", sizeof(wchar_t));
     5		
     6		#ifdef _M_IX86
     7			printf("86\n");
     8		#else
     9			printf("64\n");
    10		#endif
    11	}

#说明：文件中的空白行，nl 不会加上行号
```

* 实例二：用 nl 列出 test1.c 的内容，空本行也加上行号

```
[root@localhost test]# nl -b a test1.c
     1	#include <stdio.h>
     2	#include <stddef.h>
     3	
     4	int main() {
     5		printf("sizeof(wchar_t): %d\n", sizeof(wchar_t));
     6		
     7		#ifdef _M_IX86
     8			printf("86\n");
     9		#else
    10			printf("64\n");
    11		#endif
    12	}
```

### 实例3：让行号前面自动补上0,统一输出格式

```
[root@localhost test]# nl -b a -n rz test1.c
000001	#include <stdio.h>
000002	#include <stddef.h>
000003	
000004	int main() {
000005		printf("sizeof(wchar_t): %d\n", sizeof(wchar_t));
000006		
000007		#ifdef _M_IX86
000008			printf("86\n");
000009		#else
000010			printf("64\n");
000011		#endif
000012	}

[root@localhost test]# nl -b a -n rz -w3 test1.c
001	#include <stdio.h>
002	#include <stddef.h>
003	
004	int main() {
005		printf("sizeof(wchar_t): %d\n", sizeof(wchar_t));
006		
007		#ifdef _M_IX86
008			printf("86\n");
009		#else
010			printf("64\n");
011		#endif
012	}

# nl -b a -n rz 命令行号默认为六位，要调整位数可以加上参数 -w 3 调整为3位。
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

