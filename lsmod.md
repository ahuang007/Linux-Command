# Linux lsmod 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`lsmod = List Modules`

Linux lsmod 命令用于显示已载入系统的模块。

执行 lsmod(list modules) 指令，会列出所有已载入系统的模块。Linux 操作系统的核心具有模块化的特性，应此在编译核心时，务须把全部的功能都放入核心。您可以将这些功能编译成一个个单独的模块，待需要时再分别载入。

### 语法

```
lsmod
```

### 实例

显示模块信息

```
[app@localhost texas_poker_game_3d_gold_formal_3]$ lsmod
Module                  Size  Used by
nfnetlink_queue        18197  0 
nfnetlink_log          17892  0 
nfnetlink              14696  2 nfnetlink_log,nfnetlink_queue
bluetooth             534918  0 
fuse                   87741  3 
xt_CHECKSUM            12549  1 
iptable_mangle         12695  1 
ipt_MASQUERADE         12678  3 
nf_nat_masquerade_ipv4    13412  1 ipt_MASQUERADE
iptable_nat            12875  1 
...
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)