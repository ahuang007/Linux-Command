# Linux hwclock 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

head 命令与 [tail](https://github.com/ahuang007/Linux-Command/blob/master/tail.md) 命令用法相似，head 命令用于查看文档的开始指定数量的字符块，默认显示文档的前 10 行，如果给定的文件不止一个，则在显示的每个文件前面加一个文件名标题。

1. 用法

   head [选项] [文件..]

2. 命令选项

   -c, --bytes=[-]K 　　k,显示文档开始的前k个字节，-k,不显示文档结尾的最后 k 个字节
   -n, --lines=[-]K 　　 k,显示文档开始的前k行，-k,不显示文档结尾的最后 k 行
   -q, --quiet, --silent  不显示包含给定文件名的文件头
   -v, --verbose 　　  总是显示包含给定文件名的文件头
   --help 　　　　　 显示此帮助信息并退出
   --version 　　 　显示版本信息并退出

3. 实例

   * 显示 a.txt 前 5 行内容

   ```
   [huanglijun@localhost test]$ cat a.txt 
   1
	2
   3
   4
   5
   a
   b
   c
   d
   e
   x
   y
   z
   [huanglijun@localhost test]$ head -5 a.txt 
   1
   2
   3
   4
   5
   [huanglijun@localhost test]$ head -n 5 a.txt 
   1
   2
   3
   4
   5
   
   ```
   
   * 显示除了 a.txt 最后 10 行的内容
   
   ```
   [huanglijun@localhost test]$ head -n -10 a.txt 
   1
   2
   3
   ```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)
