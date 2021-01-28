# Linux du 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`du = Disk usage`

Linux du命令用于显示目录或文件的大小。

du会显示指定的目录或文件所占用的磁盘空间。

### 语法

```
du [-abcDhHklmsSx][-L <符号连接>][-X <文件>][--block-size][--exclude=<目录或文件>][--max-depth=<目录层数>][--help][--version][目录或文件]
```

**参数说明**：

- -a或-all 显示目录中个别文件的大小。
- -b或-bytes 显示目录或文件大小时，以byte为单位。
- -c或--total 除了显示个别目录或文件的大小外，同时也显示所有目录或文件的总和。
- -D或--dereference-args 显示指定符号连接的源文件大小。
- -h或--human-readable 以K，M，G为单位，提高信息的可读性。
- -H或--si 与-h参数相同，但是K，M，G是以1000为换算单位。
- -k或--kilobytes 以1024 bytes为单位。
- -l或--count-links 重复计算硬件连接的文件。
- -L<符号连接>或--dereference<符号连接> 显示选项中所指定符号连接的源文件大小。
- -m或--megabytes 以1MB为单位。
- -s或--summarize 仅显示总计。
- -S或--separate-dirs 显示个别目录的大小时，并不含其子目录的大小。
- -x或--one-file-xystem 以一开始处理时的文件系统为准，若遇上其它不同的文件系统目录则略过。
- -X<文件>或--exclude-from=<文件> 在<文件>指定目录或文件。
- --exclude=<目录或文件> 略过指定的目录或文件。
- --max-depth=<目录层数> 超过指定层数的目录后，予以忽略。
- --help 显示帮助。
- --version 显示版本信息。

### 实例

显示目录或者文件所占空间:

```
[root@localhost bin (server_simple ✗)]$ du
32	./runtime/center/pem/ca
16	./runtime/center/pem/server
16	./runtime/center/pem/client
68	./runtime/center/pem
97448	./runtime/center/log
97528	./runtime/center
97532	./runtime
150960	.

```

只显示当前目录下面的子目录的目录大小和当前目录的总的大小，最下面的1288为当前目录的总大小

显示指定文件所占空间

```
[root@localhost bin (server_simple ✗)]$ du game_engine     
43896	game_engine
```

方便阅读的格式显示test目录所占空间情况：

```
[root@localhost bin (server_simple ✗)]$ du -h .
32K	./runtime/center/pem/ca
16K	./runtime/center/pem/server
16K	./runtime/center/pem/client
68K	./runtime/center/pem
96M	./runtime/center/log
96M	./runtime/center
96M	./runtime
148M	.

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)