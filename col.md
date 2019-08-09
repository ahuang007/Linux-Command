### Linux col 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux col 命令用于过滤控制字符。

在许多 UNIX 说明文件里，都有 RLF 控制字符。当我们运用shell特殊字符">"和">>"，把说明文件的内容输出成纯文本文件时，控制字符会变成乱码，col 指令则能有效滤除这些控制字符。

### 语法

```
col [-bfx][-l<缓冲区列数>] 
```

**参数**：

- -b 过滤掉所有的控制字符，包括 RLF 和 HRLF。
- -f 滤除RLF字符，但允许将HRLF字符呈现出来。
- -x 以多个空格字符来表示跳格字符。
- -l<缓冲区列数> 预设的内存缓冲区有128列，您可以自行指定缓冲区的大小。

### 实例

下面以 gcc 命令帮助文档为例，讲解 col 命令的使用。

将 gcc 命令的帮助文档保存为 gcc.txt，分别是不使用 col 和 使用 col -b 参数过滤所有控制字符。

在终端中使用如下命令：

~~~markdown
man gcc > gcc.txt
```
GCC(1)                                GNU                               GCC(1)



N^HNA^HAM^HME^HE
       gcc - GNU project C and C++ compiler

S^HSY^HYN^HNO^HOP^HPS^HSI^HIS^HS
       gcc [-^H-c^Hc|-^H-S^HS|-^H-E^HE] [-^H-s^Hst^Htd^Hd=^H=_^Hs_^Ht_^Ha_^Hn_^Hd_^Ha_^Hr_^Hd]
           [-^H-g^Hg] [-^H-p^Hpg^Hg] [-^H-O^HO_^Hl_^He_^Hv_^He_^Hl]
           [-^H-W^HW_^Hw_^Ha_^Hr_^Hn...] [-^H-p^Hpe^Hed^Hda^Han^Hnt^Hti^Hic^Hc]
           [-^H-I^HI_^Hd_^Hi_^Hr...] [-^H-L^HL_^Hd_^Hi_^Hr...]
           [-^H-D^HD_^Hm_^Ha_^Hc_^Hr_^Ho[=_^Hd_^He_^Hf_^Hn]...] [-^H-U^HU_^Hm_^Ha_^Hc_^Hr_^Ho]
           [-^H-f^Hf_^Ho_^Hp_^Ht_^Hi_^Ho_^Hn...] [-^H-m^Hm_^Hm_^Ha_^Hc_^Hh_^Hi_^Hn_^He_^H-_^Ho_^Hp_^Ht_^Hi_^Ho_^Hn...]
           [-^H-o^Ho _^Ho_^Hu_^Ht_^Hf_^Hi_^Hl_^He] [@_^Hf_^Hi_^Hl_^He] _^Hi_^Hn_^Hf_^Hi_^Hl_^He...

       Only the most useful options are listed here; see below for the
       remainder.  g^Hg+^H++^H+ accepts mostly the same options as g^Hgc^Hcc^Hc.
```

man gcc | col -b > gcc1.txt
```
GCC(1)                                GNU                               GCC(1)



NAME
       gcc - GNU project C and C++ compiler

SYNOPSIS
       gcc [-c|-S|-E] [-std=standard]
           [-g] [-pg] [-Olevel]
           [-Wwarn...] [-pedantic]
           [-Idir...] [-Ldir...]
           [-Dmacro[=defn]...] [-Umacro]
           [-foption...] [-mmachine-option...]
           [-o outfile] [@file] infile...

       Only the most useful options are listed here; see below for the
       remainder.  g++ accepts mostly the same options as gcc.
```
~~~

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)