# Linux zipinfo 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux zipinfo命令用于列出压缩文件信息。

执行zipinfo指令可得知zip压缩文件的详细信息。

### 语法

```
zipinfo [-12hlmMstTvz][压缩文件][文件...][-x <范本样式>]
```

**参数**：

- -1 只列出文件名称。
- -2 此参数的效果和指定"-1"参数类似，但可搭配"-h","-t"和"-z"参数使用。
- -h 只列出压缩文件的文件名称。
- -l 此参数的效果和指定"-m"参数类似，但会列出原始文件的大小而非每个文件的压缩率。
- -m 此参数的效果和指定"-s"参数类似，但多会列出每个文件的压缩率。
- -M 若信息内容超过一个画面，则采用类似more指令的方式列出信息。
- -s 用类似执行"ls -l"指令的效果列出压缩文件内容。
- -t 只列出压缩文件内所包含的文件数目，压缩前后的文件大小及压缩率。
- -T 将压缩文件内每个文件的日期时间用年，月，日，时，分，秒的顺序列出。
- -v 详细显示压缩文件内每一个文件的信息。
- -x<范本样式> 不列出符合条件的文件的信息。
- -z 如果压缩文件内含有注释，就将注释显示出来。

### 实例

显示压缩文件信息

```
[huanglijun@localhost test]$ zipinfo test1.zip 
Archive:  test1.zip
Zip file size: 6646 bytes, number of entries: 7
drwxrwxr-x  3.0 unx        0 bx stor 20-Jan-15 18:54 test1/
-rw-rw-r--  3.0 unx       40 tx defN 19-Oct-10 09:54 test1/testf.txt
-rw-rw-r--  3.0 unx      329 tx defN 20-Jan-08 18:34 test1/a.c
-rw-rw-r--  3.0 unx      316 tx defN 20-Jan-14 16:24 test1/c.c
-rw-rw-r--  3.0 unx      306 tx defN 20-Jan-15 12:00 test1/b.c
-rw-rw-r--  3.0 unx      319 tx defN 20-Jan-15 18:54 test1/d.c
-rwxrwxr-x  3.0 unx    15528 bx defN 20-Jan-15 18:54 test1/a.out
7 files, 16838 bytes uncompressed, 5592 bytes compressed:  66.8%
```

显示压缩文件中每个文件的信息

```
[huanglijun@localhost test]$ zipinfo -v test1.zip 
Archive:  test1.zip
There is no zipfile comment.

End-of-central-directory record:
-------------------------------

  Zip archive file size:                      6646 (00000000000019F6h)
  Actual end-cent-dir record offset:          6624 (00000000000019E0h)
  Expected end-cent-dir record offset:        6624 (00000000000019E0h)
  (based on the length of the central directory and its expected offset)

  This zipfile constitutes the sole disk of a single-part archive; its
  central directory contains 7 entries.
  The central directory is 558 (000000000000022Eh) bytes long,
  and its (expected) offset in bytes from the beginning of the zipfile
  is 6066 (00000000000017B2h).


Central directory entry #1:
---------------------------

  test1/

  offset of local header from start of archive:   0
                                                  (0000000000000000h) bytes
  file system or operating system of origin:      Unix
  version of encoding software:                   3.0
  minimum file system compatibility required:     MS-DOS, OS/2 or NT FAT
  minimum software version required to extract:   1.0
  compression method:                             none (stored)
  file security status:                           not encrypted
  extended local header:                          no
  file last modified on (DOS date/time):          2020 Jan 15 18:54:50
  file last modified on (UT extra field modtime): 2020 Jan 15 18:54:50 local
  file last modified on (UT extra field modtime): 2020 Jan 15 10:54:50 UTC
  32-bit CRC value (hex):                         00000000
  compressed size:                                0 bytes
  uncompressed size:                              0 bytes
  length of filename:                             6 characters
  length of extra field:                          24 bytes
  length of file comment:                         0 characters
  disk number on which file begins:               disk 1
  apparent file type:                             binary
  Unix file attributes (040775 octal):            drwxrwxr-x
  MS-DOS file attributes (10 hex):                dir 

  The central-directory extra field contains:
  - A subfield with ID 0x5455 (universal time) and 5 data bytes.
    The local extra field has UTC/GMT modification/access times.
  - A subfield with ID 0x7875 (Unix UID/GID (any size)) and 11 data bytes:
    01 04 f2 03 00 00 04 f2 03 00 00.

  There is no file comment.

Central directory entry #2:
---------------------------

  test1/testf.txt

  offset of local header from start of archive:   64
                                                  (0000000000000040h) bytes
  file system or operating system of origin:      Unix
  version of encoding software:                   3.0
  minimum file system compatibility required:     MS-DOS, OS/2 or NT FAT
  minimum software version required to extract:   2.0
  compression method:                             deflated
  compression sub-type (deflation):               normal
  file security status:                           not encrypted
  extended local header:                          no
  file last modified on (DOS date/time):          2019 Oct 10 09:54:54
  file last modified on (UT extra field modtime): 2019 Oct 10 09:54:53 local
  file last modified on (UT extra field modtime): 2019 Oct 10 01:54:53 UTC
  32-bit CRC value (hex):                         c66e016c
  compressed size:                                39 bytes
  uncompressed size:                              40 bytes
  length of filename:                             15 characters
  length of extra field:                          24 bytes
  length of file comment:                         0 characters
  disk number on which file begins:               disk 1
  apparent file type:                             text
  Unix file attributes (100664 octal):            -rw-rw-r--
  MS-DOS file attributes (00 hex):                none

  The central-directory extra field contains:
  - A subfield with ID 0x5455 (universal time) and 5 data bytes.
    The local extra field has UTC/GMT modification/access times.
  - A subfield with ID 0x7875 (Unix UID/GID (any size)) and 11 data bytes:
    01 04 f2 03 00 00 04 f2 03 00 00.

  There is no file comment.

Central directory entry #3:
---------------------------

  test1/a.c

  offset of local header from start of archive:   176
                                                  (00000000000000B0h) bytes
  file system or operating system of origin:      Unix
  version of encoding software:                   3.0
  minimum file system compatibility required:     MS-DOS, OS/2 or NT FAT
  minimum software version required to extract:   2.0
  compression method:                             deflated
  compression sub-type (deflation):               normal
  file security status:                           not encrypted
  extended local header:                          no
  file last modified on (DOS date/time):          2020 Jan 8 18:34:00
  file last modified on (UT extra field modtime): 2020 Jan 8 18:34:00 local
  file last modified on (UT extra field modtime): 2020 Jan 8 10:34:00 UTC
  32-bit CRC value (hex):                         b4ef9724
  compressed size:                                203 bytes
  uncompressed size:                              329 bytes
  length of filename:                             9 characters
  length of extra field:                          24 bytes
  length of file comment:                         0 characters
  disk number on which file begins:               disk 1
  apparent file type:                             text
  Unix file attributes (100664 octal):            -rw-rw-r--
  MS-DOS file attributes (00 hex):                none

  The central-directory extra field contains:
  - A subfield with ID 0x5455 (universal time) and 5 data bytes.
    The local extra field has UTC/GMT modification/access times.
  - A subfield with ID 0x7875 (Unix UID/GID (any size)) and 11 data bytes:
    01 04 f2 03 00 00 04 f2 03 00 00.

  There is no file comment.

Central directory entry #4:
---------------------------

  test1/c.c

  offset of local header from start of archive:   446
                                                  (00000000000001BEh) bytes
  file system or operating system of origin:      Unix
  version of encoding software:                   3.0
  minimum file system compatibility required:     MS-DOS, OS/2 or NT FAT
  minimum software version required to extract:   2.0
  compression method:                             deflated
  compression sub-type (deflation):               normal
  file security status:                           not encrypted
  extended local header:                          no
  file last modified on (DOS date/time):          2020 Jan 14 16:24:38
  file last modified on (UT extra field modtime): 2020 Jan 14 16:24:38 local
  file last modified on (UT extra field modtime): 2020 Jan 14 08:24:38 UTC
  32-bit CRC value (hex):                         1bffd46a
  compressed size:                                184 bytes
  uncompressed size:                              316 bytes
  length of filename:                             9 characters
  length of extra field:                          24 bytes
  length of file comment:                         0 characters
  disk number on which file begins:               disk 1
  apparent file type:                             text
  Unix file attributes (100664 octal):            -rw-rw-r--
  MS-DOS file attributes (00 hex):                none

  The central-directory extra field contains:
  - A subfield with ID 0x5455 (universal time) and 5 data bytes.
    The local extra field has UTC/GMT modification/access times.
  - A subfield with ID 0x7875 (Unix UID/GID (any size)) and 11 data bytes:
    01 04 f2 03 00 00 04 f2 03 00 00.

  There is no file comment.

Central directory entry #5:
---------------------------

  test1/b.c

  offset of local header from start of archive:   697
                                                  (00000000000002B9h) bytes
  file system or operating system of origin:      Unix
  version of encoding software:                   3.0
  minimum file system compatibility required:     MS-DOS, OS/2 or NT FAT
  minimum software version required to extract:   2.0
  compression method:                             deflated
  compression sub-type (deflation):               normal
  file security status:                           not encrypted
  extended local header:                          no
  file last modified on (DOS date/time):          2020 Jan 15 12:00:54
  file last modified on (UT extra field modtime): 2020 Jan 15 12:00:54 local
  file last modified on (UT extra field modtime): 2020 Jan 15 04:00:54 UTC
  32-bit CRC value (hex):                         4e4e91a8
  compressed size:                                202 bytes
  uncompressed size:                              306 bytes
  length of filename:                             9 characters
  length of extra field:                          24 bytes
  length of file comment:                         0 characters
  disk number on which file begins:               disk 1
  apparent file type:                             text
  Unix file attributes (100664 octal):            -rw-rw-r--
  MS-DOS file attributes (00 hex):                none

  The central-directory extra field contains:
  - A subfield with ID 0x5455 (universal time) and 5 data bytes.
    The local extra field has UTC/GMT modification/access times.
  - A subfield with ID 0x7875 (Unix UID/GID (any size)) and 11 data bytes:
    01 04 f2 03 00 00 04 f2 03 00 00.

  There is no file comment.

Central directory entry #6:
---------------------------

  test1/d.c

  offset of local header from start of archive:   966
                                                  (00000000000003C6h) bytes
  file system or operating system of origin:      Unix
  version of encoding software:                   3.0
  minimum file system compatibility required:     MS-DOS, OS/2 or NT FAT
  minimum software version required to extract:   2.0
  compression method:                             deflated
  compression sub-type (deflation):               normal
  file security status:                           not encrypted
  extended local header:                          no
  file last modified on (DOS date/time):          2020 Jan 15 18:54:46
  file last modified on (UT extra field modtime): 2020 Jan 15 18:54:46 local
  file last modified on (UT extra field modtime): 2020 Jan 15 10:54:46 UTC
  32-bit CRC value (hex):                         a6c2517b
  compressed size:                                196 bytes
  uncompressed size:                              319 bytes
  length of filename:                             9 characters
  length of extra field:                          24 bytes
  length of file comment:                         0 characters
  disk number on which file begins:               disk 1
  apparent file type:                             text
  Unix file attributes (100664 octal):            -rw-rw-r--
  MS-DOS file attributes (00 hex):                none

  The central-directory extra field contains:
  - A subfield with ID 0x5455 (universal time) and 5 data bytes.
    The local extra field has UTC/GMT modification/access times.
  - A subfield with ID 0x7875 (Unix UID/GID (any size)) and 11 data bytes:
    01 04 f2 03 00 00 04 f2 03 00 00.

  There is no file comment.

Central directory entry #7:
---------------------------

  test1/a.out

  offset of local header from start of archive:   1229
                                                  (00000000000004CDh) bytes
  file system or operating system of origin:      Unix
  version of encoding software:                   3.0
  minimum file system compatibility required:     MS-DOS, OS/2 or NT FAT
  minimum software version required to extract:   2.0
  compression method:                             deflated
  compression sub-type (deflation):               normal
  file security status:                           not encrypted
  extended local header:                          no
  file last modified on (DOS date/time):          2020 Jan 15 18:54:50
  file last modified on (UT extra field modtime): 2020 Jan 15 18:54:50 local
  file last modified on (UT extra field modtime): 2020 Jan 15 10:54:50 UTC
  32-bit CRC value (hex):                         3e2099fe
  compressed size:                                4768 bytes
  uncompressed size:                              15528 bytes
  length of filename:                             11 characters
  length of extra field:                          24 bytes
  length of file comment:                         0 characters
  disk number on which file begins:               disk 1
  apparent file type:                             binary
  Unix file attributes (100775 octal):            -rwxrwxr-x
  MS-DOS file attributes (00 hex):                none

  The central-directory extra field contains:
  - A subfield with ID 0x5455 (universal time) and 5 data bytes.
    The local extra field has UTC/GMT modification/access times.
  - A subfield with ID 0x7875 (Unix UID/GID (any size)) and 11 data bytes:
    01 04 f2 03 00 00 04 f2 03 00 00.

  There is no file comment.

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)