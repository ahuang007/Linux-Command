# Linux unzip 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux unzip 命令用于解压缩 zip 文件

unzip 为 .zip 压缩文件的解压缩程序。

### 语法

```
unzip [-cflptuvz][-agCjLMnoqsVX][-P <密码>][.zip文件][文件][-d <目录>][-x <文件>] 或 unzip [-Z]
```

**参数**：

- -c 将解压缩的结果显示到屏幕上，并对字符做适当的转换。
- -f 更新现有的文件。
- -l 显示压缩文件内所包含的文件。
- -p 与-c参数类似，会将解压缩的结果显示到屏幕上，但不会执行任何的转换。
- -t 检查压缩文件是否正确。
- -u 与-f参数类似，但是除了更新现有的文件外，也会将压缩文件中的其他文件解压缩到目录中。
- -v 执行是时显示详细的信息。
- -z 仅显示压缩文件的备注文字。
- -a 对文本文件进行必要的字符转换。
- -b 不要对文本文件进行字符转换。
- -C 压缩文件中的文件名称区分大小写。
- -j 不处理压缩文件中原有的目录路径。
- -L 将压缩文件中的全部文件名改为小写。
- -M 将输出结果送到more程序处理。
- -n 解压缩时不要覆盖原有的文件。
- -o 不必先询问用户，unzip执行后覆盖原有文件。
- -P<密码> 使用zip的密码选项。
- -q 执行时不显示任何信息。
- -s 将文件名中的空白字符转换为底线字符。
- -V 保留VMS的文件版本信息。
- -X 解压缩时同时回存文件原来的UID/GID。
- [.zip文件] 指定.zip压缩文件。
- [文件] 指定要处理.zip压缩文件中的哪些文件。
- -d<目录> 指定文件解压缩后所要存储的目录。
- -x<文件> 指定不要处理.zip压缩文件中的哪些文件。
- -Z unzip -Z等于执行zipinfo指令。

### 实例

查看压缩文件中包含的文件：

```
[huanglijun@localhost test]$ unzip -l test1.zip 
Archive:  test1.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
        0  01-15-2020 18:54   test1/
       40  10-10-2019 09:54   test1/testf.txt
      329  01-08-2020 18:34   test1/a.c
      316  01-14-2020 16:24   test1/c.c
      306  01-15-2020 12:00   test1/b.c
      319  01-15-2020 18:54   test1/d.c
    15528  01-15-2020 18:54   test1/a.out
---------                     -------
    16838                     7 files
```

-v 参数用于查看压缩文件目录信息，但是不解压该文件。

```
[huanglijun@localhost test]$ unzip -v test1.zip 
Archive:  test1.zip
 Length   Method    Size  Cmpr    Date    Time   CRC-32   Name
--------  ------  ------- ---- ---------- ----- --------  ----
       0  Stored        0   0% 01-15-2020 18:54 00000000  test1/
      40  Defl:N       39   3% 10-10-2019 09:54 c66e016c  test1/testf.txt
     329  Defl:N      203  38% 01-08-2020 18:34 b4ef9724  test1/a.c
     316  Defl:N      184  42% 01-14-2020 16:24 1bffd46a  test1/c.c
     306  Defl:N      202  34% 01-15-2020 12:00 4e4e91a8  test1/b.c
     319  Defl:N      196  39% 01-15-2020 18:54 a6c2517b  test1/d.c
   15528  Defl:N     4768  69% 01-15-2020 18:54 3e2099fe  test1/a.out
--------          -------  ---                            -------
   16838             5592  67%                            7 files
```

-d 参数用于指定解压目录

```
[huanglijun@localhost ~]$ unzip test1.zip -d test2
Archive:  test1.zip
   creating: test2/test1/
  inflating: test2/test1/testf.txt   
  inflating: test2/test1/a.c         
  inflating: test2/test1/c.c         
  inflating: test2/test1/b.c         
  inflating: test2/test1/d.c         
  inflating: test2/test1/a.out
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

