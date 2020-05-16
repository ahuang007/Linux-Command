# Linux sed 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`sed = Stream Editor`

Linux sed 命令是利用脚本来处理文本文件。

sed 可依照脚本的指令来处理、编辑文本文件。

Sed 主要用来自动编辑一个或多个文件、简化对文件的反复操作、编写转换程序等。

### 语法

```
sed [-hnV][-e<script>][-f<script文件>][文本文件]
```

**参数说明**：

- -e<script>或--expression=<script> 以选项中指定的script来处理输入的文本文件。
- -f<script文件>或--file=<script文件> 以选项中指定的script文件来处理输入的文本文件。
- -h或--help 显示帮助。
- -n或--quiet或--silent 仅显示script处理后的结果。
- -V或--version 显示版本信息。

**动作说明**：

- a ：新增， a 的后面可以接字串，而这些字串会在新的一行出现(目前的下一行)～
- c ：取代， c 的后面可以接字串，这些字串可以取代 n1,n2 之间的行！
- d ：删除，因为是删除啊，所以 d 后面通常不接任何咚咚；
- i ：插入， i 的后面可以接字串，而这些字串会在新的一行出现(目前的上一行)；
- p ：打印，亦即将某个选择的数据印出。通常 p 会与参数 sed -n 一起运行～
- s ：取代，可以直接进行取代的工作哩！通常这个 s 的动作可以搭配正规表示法！例如 1,20s/old/new/g 就是啦！

### 实例

在testfile文件的第四行后添加一行，并将结果输出到标准输出，在命令行提示符下输入如下命令：

```
sed -e 4a\newLine testfile 
```

首先查看testfile中的内容如下：

```
[root@localhost test ]$ cat testfile 
abc
123
def
4
qw
```

使用sed命令后，输出结果如下：

```
[root@localhost test ]$ sed -e 4a\HelloWorld testfile 
abc
123
def
4
HelloWorld
qw
```

### 以行为单位的新增/删除

将 /etc/passwd 的内容列出并且列印行号，同时，请将第 3~45 行删除！

```
[root@localhost test ]$ nl /etc/passwd | sed '3,45d'
     1	root:x:0:0:root:/root:/bin/zsh
     2	bin:x:1:1:bin:/bin:/sbin/nologin
    46	oprofile:x:16:16:Special user account to be used by OProfile:/var/lib/oprofile:/sbin/nologin
    47	tcpdump:x:72:72::/:/sbin/nologin
    48	lm56:x:1000:1000:lm56:/home/lm56:/bin/bash

```

sed 的动作为 '3,45d' ，那个 d 就是删除！因为 3-45 行给他删除了，所以显示的数据就没有 3-45 行～ 另外，注意一下，原本应该是要下达 sed -e 才对，没有 -e 也行啦！同时也要注意的是， sed 后面接的动作，请务必以 '' 两个单引号括住喔！

只要删除第 2 行

```
[root@localhost test ]$ nl /etc/passwd | sed '2d'   
     1	root:x:0:0:root:/root:/bin/zsh
     3	daemon:x:2:2:daemon:/sbin:/sbin/nologin
		......
```

要删除第 3 到最后一行

```
[root@localhost test ]$ nl /etc/passwd | sed '3,$d'
     1	root:x:0:0:root:/root:/bin/zsh
     2	bin:x:1:1:bin:/bin:/sbin/nologin
```

在第二行后(亦即是加在第三行)加上 Hello world! 字样！

```
[root@localhost test ]$ nl /etc/passwd | sed '2a Hello world!'
     1	root:x:0:0:root:/root:/bin/zsh
     2	bin:x:1:1:bin:/bin:/sbin/nologin
Hello world!
     3	daemon:x:2:2:daemon:/sbin:/sbin/nologin
     4	adm:x:3:4:adm:/var/adm:/sbin/nologin
		......
```

那如果是要在第二行前

```
[root@localhost test ]$ nl /etc/passwd | sed '2i Hello world!'
     1	root:x:0:0:root:/root:/bin/zsh
Hello world!
     2	bin:x:1:1:bin:/bin:/sbin/nologin
		......
```

如果是要增加两行以上，在第二行后面加入两行字，例如 **Tea?** 与 **Coffee?**

```
[root@localhost test ]$ nl /etc/passwd | sed '2a Tea? \
> Coffe?'
     1	root:x:0:0:root:/root:/bin/zsh
     2	bin:x:1:1:bin:/bin:/sbin/nologin
Tea? 
Coffe?
     3	daemon:x:2:2:daemon:/sbin:/sbin/nologin
		......
```

每一行之间都必须要以反斜杠 "\\"来进行新行的添加喔！所以，上面的例子中，我们可以发现在第一行的最后面就有 \ 存在。

### 以行为单位的替换与显示

将第2-5行的内容取代成为 "No 2-5 number"

```
[root@localhost test ]$ nl /etc/passwd | sed '2,5c No 2-5 number' 
     1	root:x:0:0:root:/root:/bin/zsh
No 2-5 number
     6	sync:x:5:0:sync:/sbin:/bin/sync
     7	shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
		......
```

透过这个方法我们就能够将数据整行取代了！

仅列出 /etc/passwd 文件内的第 5-7 行

```
[root@localhost test ]$ nl /etc/passwd | sed -n '5,7p'
     5	lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
     6	sync:x:5:0:sync:/sbin:/bin/sync
     7	shutdown:x:6:0:shutdown:/sbin:/sbin/shutdown
```

可以透过这个 sed 的以行为单位的显示功能， 就能够将某一个文件内的某些行号选择出来显示。

### 数据的搜寻并显示

搜索 /etc/passwd有root关键字的行

```
[root@localhost test ]$ nl /etc/passwd | sed '/root/p'
     1	root:x:0:0:root:/root:/bin/zsh
     1	root:x:0:0:root:/root:/bin/zsh
     2	bin:x:1:1:bin:/bin:/sbin/nologin
     3	daemon:x:2:2:daemon:/sbin:/sbin/nologin
     4	adm:x:3:4:adm:/var/adm:/sbin/nologin
	......
```

如果root找到，除了输出所有行，还会输出匹配行。

使用-n的时候将只打印包含模板的行。

```
[root@localhost test ]$ nl /etc/passwd | sed -n '/root/p'
     1	root:x:0:0:root:/root:/bin/zsh
    10	operator:x:11:0:operator:/root:/sbin/nologin
```

### 数据的搜寻并删除

删除/etc/passwd所有包含root的行，其他行输出

```
[root@localhost test ]$ nl /etc/passwd | sed  '/root/d'
     2	bin:x:1:1:bin:/bin:/sbin/nologin
     3	daemon:x:2:2:daemon:/sbin:/sbin/nologin
     4	adm:x:3:4:adm:/var/adm:/sbin/nologin
     5	lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin
     ......
```

### 数据的搜寻并执行命令

搜索/etc/passwd,找到root对应的行，执行后面花括号中的一组命令，每个命令之间用分号分隔，这里把bash替换为zsh，再输出这行：

```
[root@localhost test ]$ nl /etc/passwd | sed -n '/root/{s/bash/zsh/;p;q}'    
     1	root:x:0:0:root:/root:/bin/zsh
```

最后的q是退出。

### 数据的搜寻并替换

除了整行的处理模式之外， sed 还可以用行为单位进行部分数据的搜寻并取代。基本上 sed 的搜寻与替代的与 vi 相当的类似！他有点像这样：

```
sed 's/要被取代的字串/新的字串/g'
```

先观察原始信息，利用 /sbin/ifconfig 查询 IP

```
root@localhost test ]$ /sbin/ifconfig eth0
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.11.233  netmask 255.255.248.0  broadcast 192.168.15.255
        inet6 fe80::21c:42ff:fef8:20d9  prefixlen 64  scopeid 0x20<link>
        ether 00:1c:42:f8:20:d9  txqueuelen 1000  (Ethernet)
        RX packets 56557103  bytes 18611095875 (17.3 GiB)
        RX errors 0  dropped 4  overruns 0  frame 0
        TX packets 9903052  bytes 29992939937 (27.9 GiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

本机的ip是192.168.11.233。

将 IP 前面的部分予以删除

```
[root@localhost test ]$ /sbin/ifconfig eth0 | grep 'inet' | grep -v 'inet6' | sed 's/inet//g' 
         192.168.11.233  netmask 255.255.248.0  broadcast 192.168.15.255
```

接下来则是删除后续的部分，亦即：192.168.11.233  netmask 255.255.248.0  broadcast 192.168.15.255

将 IP 后面的部分予以删除

```
[root@localhost test ]$ /sbin/ifconfig eth0 | grep 'inet' | grep -v 'inet6' | sed 's/inet//g' | sed 's/netmask.*$//g'
         192.168.11.233  
```

### 多点编辑

一条sed命令，删除/etc/passwd第三行到末尾的数据，并把bash替换为 zsh

```
[root@localhost test ]$ nl /etc/passwd | sed -e '3,$d' -e 's/bash/zsh/'      
     1	root:x:0:0:root:/root:/bin/zsh
     2	bin:x:1:1:bin:/bin:/sbin/nologin
```

-e表示多点编辑，第一个编辑命令删除/etc/passwd第三行到末尾的数据，第二条命令搜索bash替换为blueshell。

### 直接修改文件内容(危险动作)

sed 可以直接修改文件的内容，不必使用管道命令或数据流重导向！ 不过，由於这个动作会直接修改到原始的文件，所以请你千万不要随便拿系统配置来测试！ 我们还是使用文件 regular_express.txt 文件来测试看看吧！

testfile 文件内容如下：

```
[root@localhost test ]$ cat testfile                 
aaa
123
aaa
4
aa
```

利用 sed 将 testfile 内每一行结尾若为 . 则换成 !

```
[root@localhost test ]$ sed -i 's/a/x/g' testfile
[root@localhost test ]$ cat testfile             
xbc
123
xde
4
xx
```

利用 sed 直接在 testfile 最后一行加入 **# This is a test**:

```
[root@localhost test ]$ sed -i '$a # This is a test' testfile
[root@localhost test ]$ cat testfile                         
xbc
123
xde
4
xx

# This is a test
```

由於 $ 代表的是最后一行，而 a 的动作是新增，因此该文件最后新增 **# This is a test**！

sed 的 **-i** 选项可以直接修改文件内容，这功能非常有帮助！举例来说，如果你有一个 100 万行的文件，你要在第 100 行加某些文字，此时使用 vim 可能会疯掉！因为文件太大了！那怎办？就利用 sed 啊！透过 sed 直接修改/取代的功能，你甚至不需要使用 vim 去修订！

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)