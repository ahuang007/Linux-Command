# Linux ls 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`ls = list`

* 注： ll 不是  linux  命令  `ll = ls -l ` 相当于快捷方式

Linux ls命令用于显示指定工作目录下之内容（列出目前工作目录所含之文件及子目录)。

### 语法

```
 ls [-alrtAFR] [name...]
```

**参数** :

- -a 显示所有文件及目录 (ls内定将文件名或目录名称开头为"."的视为隐藏档，不会列出)
- -l 除文件名称外，亦将文件型态、权限、拥有者、文件大小等资讯详细列出
- -r 将文件以相反次序显示(原定依英文字母次序)
- -t 将文件依建立时间之先后次序列出
- -A 同 -a ，但不列出 "." (目前目录) 及 ".." (父目录)
- -F 在列出的文件名称后加一符号；例如可执行档则加 "*", 目录则加 "/"
- -R 若目录下有文件，则以下之文件亦皆依序列出

### 实例

列出根目录(\)下的所有目录：

```
[huanglijun@localhost ~]$ ls /
boot dev  home  lib64  mnt  proc  run   srv  tmp  var
bin  etc  lib   media  opt  root  sbin  sys  usr
```

列出目前工作目录下所有名称是 s 开头的文件，越新的排越后面 :

```
[huanglijun@localhost ~]$ ls -ltr S*
-rwxr--r-- 1 huanglijun huanglijun 70 5月  25 14:01 SvnUpdate.bat
```

将 /bin 目录以下所有目录及文件详细资料列出 :

```
[huanglijun@localhost project]$ ll -lR /bin
lrwxrwxrwx. 1 root root 7 1月   3 2019 /bin -> usr/bin
```

列出目前工作目录下所有文件及目录；目录于名称后加 "/", 可执行档于名称后加 "*" :

```
[root@server skynet-accountserver (master)]$ ls -AF
.git/       .idea/     README.md*  common/  luaclib/  lualib-src/  service/  skynet/
.gitignore  Makefile*  busilog/    log/     lualib/   release/     sh/
```

查看当前目录文件属性 ll

```
[huanglijun@localhost ~]$ ll
总用量 8
drwxr-xr-x  7 huanglijun huanglijun   78 6月  28 09:37 linux
drwxr-xr-x 32 huanglijun huanglijun 4096 7月  29 10:30 protocol
-rwxr--r--  1 huanglijun huanglijun   70 5月  25 14:01 SvnUpdate.bat
-rwxr-xr-x  1 huanglijun huanglijun    0 8月  12 10:08 test.txt
```

第一个d 标识是否为文件夹

后面分别为  User、Group、及 Other 的权限。 

r 可读 w 可写 x 可执行 - 表示无 

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)