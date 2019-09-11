# Linux mkdir 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`mkdir = make directory`

Linux mkdir 命令用于建立名称为 dirName 之子目录。

### 语法

```
mkdir [-p] dirName
```

**参数说明**：

- -p 确保目录名称存在，不存在的就建一个。

### 实例

在工作目录下，建立一个名为 d1 的子目录 :

```
[huanglijun@localhost test]$ mkdir d1
[huanglijun@localhost test]$ ls -l
总用量 148
-rw-rw-r-- 1 huanglijun huanglijun 132583 9月   3 20:25 boot.txt.bak
drwxrwxr-x 2 huanglijun huanglijun      6 9月  11 11:02 d1
-rw-rw-r-- 1 huanglijun huanglijun     28 9月   5 17:36 testfile_1
-rw-rw-r-- 1 huanglijun huanglijun     41 9月   5 17:35 testfile_1_bak
-rw-rw-r-- 1 huanglijun huanglijun     32 8月  14 09:39 testfile_2
-rw-rw-r-- 1 huanglijun huanglijun     41 8月  14 09:41 testfile_3
-rw------- 1 huanglijun huanglijun      0 9月  11 10:55 tmp.aKFu
```

在工作目录下的 A 目录中，建立一个名为 B 的子目录。 若 A 目录原本不存在，则建立一个。（注：本例若不加 -p，且原本 A 目录不存在，则产生错误。）

```
[huanglijun@localhost test]$ mkdir  A/B
mkdir: 无法创建目录"A/B": 没有那个文件或目录
[huanglijun@localhost test]$ mkdir -p A/B # 成功建立A目录和A的子目录B
[huanglijun@localhost test]$ ll
总用量 148
drwxrwxr-x 3 huanglijun huanglijun     15 9月  11 11:04 A
-rw-rw-r-- 1 huanglijun huanglijun 132583 9月   3 20:25 boot.txt.bak
drwxrwxr-x 2 huanglijun huanglijun      6 9月  11 11:02 d1
-rw-rw-r-- 1 huanglijun huanglijun     28 9月   5 17:36 testfile_1
-rw-rw-r-- 1 huanglijun huanglijun     41 9月   5 17:35 testfile_1_bak
-rw-rw-r-- 1 huanglijun huanglijun     32 8月  14 09:39 testfile_2
-rw-rw-r-- 1 huanglijun huanglijun     41 8月  14 09:41 testfile_3
-rw------- 1 huanglijun huanglijun      0 9月  11 10:55 tmp.aKFu
[huanglijun@localhost test]$ ll A
总用量 0
drwxrwxr-x 2 huanglijun huanglijun 6 9月  11 11:04 B
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)