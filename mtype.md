# Linux mtype 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

mtype 为 [mtools](https://github.com/ahuang007/Linux-Command/blob/master/mtools.md) 工具指令，模拟 MS-DOS 的 type 指令，可显示 MS-DOS 文件的内容。

### 语法

```
mtype [-st][文件]
```

**参数说明**：

- -s 去除8位字符码集的第一个位，使它兼容于7位的 ASCII。
- -t 将 MS-DOS 文本文件中的"换行+光标移至行首"字符转换成 Linux 的换行字符。

### 实例

打开名为 main.c 的 MS-DOS 文件可使用如下命令：

```
[root@localhost test ]$ mtype main.c 
#include <stdio.h>

int main(){
    printf("hell world\n");
    return 0;
}

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)