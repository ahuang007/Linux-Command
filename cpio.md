# Linux cpio 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux cpio命令用于备份文件。

cpio 是用来建立，还原备份档的工具程序，它可以加入，解开 cpio 或 tar 备份档内的文件。

### 语法

```
cpio [-0aABckLovV][-C <输入/输出大小>][-F <备份档>][-H <备份格式>][-O <备份档>][--block-size=<区块大小>][--force-local][--help][--quiet][--version] 或 cpio [-bBcdfikmnrsStuvV][-C <输入/输出大小>][-E <范本文件>][-F <备份档>][-H <备份格式>][-I <备份档>][-M <回传信息>][-R <拥有者><:/.><所属群组>][--block-size=<区块大小>][--force-local][--help][--no-absolute-filenames][--no-preserve-owner][--only-verify-crc][--quiet][--sparse][--version][范本样式...] 或 cpio [-0adkiLmpuvV][-R <拥有者><:/.><所属群组>][--help][--no-preserve-owner][--quiet][--sparse][--version][目的目]
```

**参数**：

- -0或--null 　接受新增列控制字符，通常配合find指令的"-print0"参数使用。
- -a或--reset-access-time 　重新设置文件的存取时间。
- -A或--append 　附加到已存在的备份档中，且这个备份档必须存放在磁盘上，而不能放置于磁带机里。
- -b或--swap 　此参数的效果和同时指定"-sS"参数相同。
- -B 　将输入/输出的区块大小改成5210 Bytes。
- -c 　使用旧ASCII备份格式。
- -C<区块大小>或--io-size=<区块大小> 　设置输入/输出的区块大小，单位是Byte。
- -d或--make-directories 　如有需要cpio会自行建立目录。
- -E<范本文件>或--pattern-file=<范本文件> 　指定范本文件，其内含有一个或多个范本样式，让cpio解开符合范本条件的文件，格式为每列一个范本样式。
- -f或--nonmatching 　让cpio解开所有不符合范本条件的文件。
- -F<备份档>或--file=<备份档> 　指定备份档的名称，用来取代标准输入或输出，也能借此通过网络使用另一台主机的保存设备存取备份档。
- -H<备份格式> 　指定备份时欲使用的文件格式。
- -i或--extract 　执行copy-in模式，还原备份档。
- -l<备份档> 　指定备份档的名称，用来取代标准输入，也能借此通过网络使用另一台主机的保存设备读取备份档。
- -k 　此参数将忽略不予处理，仅负责解决cpio不同版本间的兼容性问题。
- -l或--link 　以硬连接的方式取代复制文件，可在copy-pass模式下运用。
- -L或--dereference 　不建立符号连接，直接复制该连接所指向的原始文件。
- -m或preserve-modification-time 　不去更换文件的更改时间。
- -M<回传信息>或--message=<回传信息> 　设置更换保存媒体的信息。
- -n或--numeric-uid-gid 　使用"-tv"参数列出备份档的内容时，若再加上参数"-n"，则会以用户识别码和群组识别码替代拥有者和群组名称列出文件清单。
- -o或--create 　执行copy-out模式，建立备份档。
- -O<备份档> 　指定备份档的名称，用来取代标准输出，也能借此通过网络　使用另一台主机的保存设备存放备份档。
- -p或--pass-through 　执行copy-pass模式，略过备份步骤，直接将文件复制到目的目录。
- -r或--rename 　当有文件名称需要更动时，采用互动模式。
- -R<拥有者><:/.><所属群组>或
- ----owner<拥有者><:/.><所属群组> 　在copy-in模式还原备份档，或copy-pass模式复制文件时，可指定这些备份，复制的文件的拥有者与所属群组。
- -s或--swap-bytes 　交换每对字节的内容。
- -S或--swap-halfwords 　交换每半个字节的内容。
- -t或--list 　将输入的内容呈现出来。
- -u或--unconditional 　置换所有文件，不论日期时间的新旧与否，皆不予询问而直接覆盖。
- -v或--verbose 　详细显示指令的执行过程。
- -V或--dot 　执行指令时，在每个文件的执行程序前面加上"."号
- --block-size=<区块大小> 　设置输入/输出的区块大小，假如设置数值为5，则区块大小为2500，若设置成10，则区块大小为5120，依次类推。
- --force-local 　强制将备份档存放在本地主机。
- --help 　在线帮助。
- --no-absolute-filenames 　使用相对路径建立文件名称。
- --no-preserve-owner 　不保留文件的拥有者，谁解开了备份档，那些文件就归谁所有。
- -only-verify-crc 　当备份档采用CRC备份格式时，可使用这项参数检查备份档内的每个文件是否正确无误。
- --quiet 　不显示复制了多少区块。
- --sparse 　倘若一个文件内含大量的连续0字节，则将此文件存成稀疏文件。
- --version 　显示版本信息。

### 实例

制作备份文件

```
[root@localhost test]# ll
total 36
-rwxr-xr-x 1 root root 8152 Dec  7 12:20 a.out
-rw-r--r-- 1 root root 3491 Nov 24 11:08 enumtype.h
-rw-r--r-- 1 root root  175 Dec  7 12:20 test1.c
-rwxr-xr-x 1 root root   99 Dec  9 11:53 test1.sh
-rwxr-xr-x 1 root root   75 Dec  9 11:56 test2.sh
-rwxr-xr-x 1 root root   77 Dec  9 12:05 test3.sh
-rw-r--r-- 1 root root  625 Dec 14 19:14 test.c
-rwxr-xr-x 1 root root   59 Dec  9 11:54 test.sh

[root@localhost test]# ls | cpio -o >bak.cpio
cpio: File bak.cpio grew, 8192 new bytes not copied
41 blocks

[root@localhost test]# ll
total 60
-rwxr-xr-x 1 root root  8152 Dec  7 12:20 a.out
-rw-r--r-- 1 root root 20992 Dec 30 11:23 bak.cpio
-rw-r--r-- 1 root root  3491 Nov 24 11:08 enumtype.h
-rw-r--r-- 1 root root   175 Dec  7 12:20 test1.c
-rwxr-xr-x 1 root root    99 Dec  9 11:53 test1.sh
-rwxr-xr-x 1 root root    75 Dec  9 11:56 test2.sh
-rwxr-xr-x 1 root root    77 Dec  9 12:05 test3.sh
-rw-r--r-- 1 root root   625 Dec 14 19:14 test.c
-rwxr-xr-x 1 root root    59 Dec  9 11:54 test.sh

```

解压缩备份文件，并列出详细信息

```
[root@localhost test]# ls | cpio -t -I bak.cpio 
a.out
bak.cpio
enumtype.h
test1.c
test1.sh
test2.sh
test3.sh
test.c
test.sh
41 blocks
```

强制解压缩

```
[root@localhost test]# cpio -i -u -I bak.cpio 
41 blocks
```

从标准输入备份文件

```
[root@localhost test]# cpio -o > tmp.cpio
test1.sh  //用户输入
test2.sh
test3.sh //按下Ctrl+D完成输入
1 block
```

复制文件

```
[root@localhost test]# cpio -p ./tmp
test1.sh  //用户输入
test2.sh
test3.sh  //按下Ctrl+D完成输入
3 block
[root@localhost test]# ll tmp
total 12
-rwxr-xr-x 1 root root 99 Dec 30 11:32 test1.sh
-rwxr-xr-x 1 root root 75 Dec 30 11:33 test2.sh
-rwxr-xr-x 1 root root 77 Dec 30 11:33 test3.sh
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)