# Linux cd 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`cd = Change directory`

Linux cd 命令用于切换当前工作目录至 dirName(目录参数)。

其中 dirName 表示法可为绝对路径或相对路径。若目录名称省略，则变换至使用者的 home 目录 (也就是刚 login 时所在的目录)。

另外，"~" 也表示为 home 目录 的意思，"." 则是表示目前所在的目录，".." 则表示目前目录位置的上一层目录。

### 语法

```
cd [dirName]
```

- dirName：要切换的目标目录。

### 实例

跳到 /usr/bin/ :

```
[huanglijun@localhost ~]$ cd /usr/bin/
[huanglijun@localhost bin]$ pwd
/usr/bin
```

跳到自己的 home 目录 :

```
[huanglijun@localhost bin]$ cd ~
[huanglijun@localhost ~]$ pwd
/home/huanglijun
```

跳到目前目录的上上两层 :

```
[huanglijun@localhost ~]$ cd ../..
[huanglijun@localhost /]$ pwd
/
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)