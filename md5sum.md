# Linux md5sum 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

相似指令 [cksum](https://github.com/ahuang007/Linux-Command/blob/master/cksum.md)

MD5算法常常被用来验证网络文件传输的完整性，防止文件被人篡改。MD5 全称是报文摘要算法（Message-Digest Algorithm 5），此算法对任意长度的信息逐位进行计算，产生一个二进制长度为128位（十六进制长度就是32位）的“指纹”（或称“报文摘要”），不同的文件产生相同的报文摘要的可能性是非常非常之小的。

md5sum命令采用MD5报文摘要算法（128位）计算和检查文件的校验和。一般来说，安装了Linux后，就会有md5sum这个工具，直接在命令行终端直接运行。

**语法**

```
`# md5sum(选项)(参数)`
```

**选项**

```
-b或--binary:  把输入文件作为二进制文件看待。
-t或--text:    把输入的文件作为文本文件看待（默认）。
-c或--check:   用来从文件中读取md5信息检查文件的一致性。(不细说了参见info)
--status:      这个选项和check一起使用,在check的时候，不输出，而是根据返回值表示检查结果。
-w或--warn:    在check的时候，检查输入的md5信息又没有非法的行，如果有则输出相应信息。`
```

**参数**

```
`文件：指定保存着文件名和校验和的文本文件`
```

**示例**
**1) 查看一个字符串的md5值** 
linux终端里查看出来的md5值都是"32位小写"格式的值

```
[huanglijun@localhost bin]$ echo -n "hello world" | md5sum
5eb63bbbe01eeed093cb22bb8f5acdc3  -
[huanglijun@localhost bin]$ echo -n "hello world" | md5sum | cut -d" " -f1
5eb63bbbe01eeed093cb22bb8f5acdc3
```

命令解释：
**md5sum** : 显示或检查 MD5(128-bit) 校验和,若没有文件选项，或者文件处为"-"，则从标准输入读取。
**echo -n** : 不打印换行符。(注意: echo -n 后面的-n参数必须加上, 这样算出的字符串的md5值才正确)
**cut** : cut用来从标准输入或文本文件中剪切列或域。剪切文本可以将之粘贴到一个文本文件。 

​		-d 指定与空格和tab键不同的域分隔符。

​		-f1 表示第一个域。

**2) 查看一个文件的md5值**

```
[huanglijun@localhost bin]$ echo "test md5" > test.txt
# 查看并获取这个文件的MD5值
[huanglijun@localhost bin]$ md5sum test.txt 
170ecb8475ca6e384dbd74c17e165c9e  test.txt
[huanglijun@localhost bin]$ md5sum test.txt | cut -d" " -f1
170ecb8475ca6e384dbd74c17e165c9e
#生成这个文件的MD5值
[huanglijun@localhost bin]$ md5sum test.txt > test.txt.md5
# 检查两个文件是否一样，可通过比较2个文件的MD5值（后续可以用这个方法校验text.txt文件是否被修改）
[huanglijun@localhost bin]$ md5sum test.txt
170ecb8475ca6e384dbd74c17e165c9e  test.txt
[huanglijun@localhost bin]$ cat test.txt.md5 
170ecb8475ca6e384dbd74c17e165c9e  test.txt
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

