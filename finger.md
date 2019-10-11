# Linux finger 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

注：`finger 不是 linux 自带指令 软件安装：yum install finger `

Linux finger 命令可以让使用者查询一些其他使用者的资料。会列出来的资料有：

- Login Name
- User Name
- Home directory
- Shell
- Login status
- mail status
- .plan
- .project
- .forward

其中 .plan、.project 和 .forward 就是使用者在他的 Home Directory 里的 .plan ， .project 和 .forward 等档案里的资料。如果没有就没有。finger 指令并不限定于在同一服务器上查询，也可以寻找某一个远端服务器上的使用者。只要给一个像是 E-mail address 一般的地址即可。

使用权限：所有使用者。

### 语法

```
finger [options] user[@address]
```

**参数说明**：

- -l 　多行显示。
- -s 　单行显示。这个选项只显示登入名称、真实姓名、终端机名称、闲置时间、登入时间、办公室号码及电话号码。如果所查询的使用者是远端服务器的使用者，这个选项无效。

### 实例

列出当前登录用户的相关信息

```
[root@server ~ ]$ finger -l // 显示用户信息
Login: root           			Name: root
Directory: /root                    	Shell: /bin/zsh
On since Tue Oct  8 09:59 (CST) on tty1 from :0
    4 minutes 4 seconds idle
On since Tue Oct  8 10:00 (CST) on pts/0 from :0.0
   2 minutes 37 seconds idle
On since Tue Oct  8 10:02 (CST) on pts/1 from 192.168.10.252
New mail received Mon Jul 16 11:01 2018 (CST)
     Unread since Sat Sep 23 18:41 2017 (CST)
No Plan.

```

显示指定用户信息

```
[app@localhost ~]$ finger -m huanglijun // 指定用户
Login: huanglijun     			Name: 
Directory: /home/huanglijun         	Shell: /bin/bash
On since 二 10月  8 09:50 (CST) on pts/4 from 192.168.10.252
   16 minutes 29 seconds idle
On since 二 10月  8 09:56 (CST) on pts/5 from 192.168.10.252
   6 minutes 13 seconds idle
Last login 二 10月  8 10:06 (CST) on pts/6 from 192.168.10.252
No mail.
No Plan.


```

下列指令可以查询本机管理员的资料：

```
[app@localhost ~]$ finger root
Login: root           			Name: root
Directory: /root                    	Shell: /bin/bash
Last login 一 9月  2 15:56 (CST) on pts/10
New mail received 三 9月  4 16:01 2019 (CST)
     Unread since 四 1月  3 16:22 2019 (CST)
No Plan.
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)