# Linux eval 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux eval 命令用于重新运算求出参数的内容。

eval 可读取一连串的参数，然后再依参数本身的特性来执行。

### 语法

```
eval [参数]
```

**参数说明**：参数不限数目，彼此之间用分号分开。

### 实例

连接多个命令

```
[huanglijun@localhost test]$ eval ll -a;free;df
总用量 8
drwxrwxr-x  2 huanglijun huanglijun  32 9月  20 09:51 .
drwx------ 12 huanglijun huanglijun 280 9月  23 11:51 ..
-rw-rw-r--  1 huanglijun huanglijun  12 9月  20 09:53 file1
-rw-rw-r--  1 huanglijun huanglijun  12 9月  20 09:53 file2
              total        used        free      shared  buff/cache   available
Mem:       32708808     4605020     4721168     6250120    23382620    21337568
Swap:      16449532     1591996    14857536
文件系统                 1K-块      已用       可用 已用% 挂载点
/dev/mapper/cl-root   52403200  19865964   32537236   38% /
devtmpfs              16338204         0   16338204    0% /dev
tmpfs                 16354404        84   16354320    1% /dev/shm
tmpfs                 16354404    215976   16138428    2% /run
tmpfs                 16354404         0   16354404    0% /sys/fs/cgroup
/dev/sda2              1038336    169596     868740   17% /boot
/dev/sda1               204580      9672     194908    5% /boot/efi
/dev/mapper/cl-home 2126530044 102094648 2024435396    5% /home
tmpfs                  3270884        16    3270868    1% /run/user/42
tmpfs                  3270884         0    3270884    0% /run/user/1001
tmpfs                  3270884         0    3270884    0% /run/user/1017
tmpfs                  3270884         0    3270884    0% /run/user/1020
tmpfs                  3270884         0    3270884    0% /run/user/1015
tmpfs                  3270884         0    3270884    0% /run/user/1010
tmpfs                  3270884         0    3270884    0% /run/user/1018

# 同时将三个命令的结果连着显示在一起
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)