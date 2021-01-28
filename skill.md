# Linux skill 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux skill 命令送个讯号给正在执行的程序，预设的讯息为 TERM (中断)，较常使用的讯息为 HUP、INT、KILL、STOP、CONT 和 0。

讯息有三种写法：分别为 -9、-SIGKILL、-KILL，可以使用 -l 或 -L 已列出可使用的讯息。

使用权限：所有使用者。

其他相关的命令：[kill](https://github.com/ahuang007/Linux-Command/blob/master/kill.md)

### 语法

```
skill [signal to send] [options] 选择程序的规则
```

**一般参数**：

- -f 快速模式/尚未完成
- -i 互动模式/ 每个动作将要被确认
- -v 详细输出/ 列出所选择程序的资讯
- -w 智能警告讯息/ 尚未完成
- -n 没有动作/ 显示程序代号

**参数**：选择程序的规则可以是：终端机代号、使用者名称、程序代号、命令名称。

- -t 终端机代号 ( tty 或 pty )
- -u 使用者名称
- -p 程序代号 ( pid )
- -c 命令名称可使用的讯号

以下列出已知的讯号名称、讯号代号、功能。

| 名称（代号） | 功能/描述                                   |
| :----------- | :------------------------------------------ |
| ALRM 14      | 离开                                        |
| HUP 1        | 离开                                        |
| INT 2        | 离开                                        |
| KILL 9       | 离开/强迫关闭                               |
| PIPE 13      | 离开                                        |
| POLL         | 离开                                        |
| PROF         | 离开                                        |
| TERM 15      | 离开                                        |
| USR1         | 离开                                        |
| USR2         | 离开                                        |
| VTALRM       | 离开                                        |
| STKFLT       | 离开/只适用于i386、m68k、arm 和 ppc 硬件    |
| UNUSED       | 离开/只适用于i386、m68k、arm 和 ppc 硬件    |
| TSTP         | 停止/产生与内容相关的行为                   |
| TTIN         | 停止/产生与内容相关的行为                   |
| TTOU         | 停止/产生与内容相关的行为                   |
| STOP         | 停止/强迫关闭                               |
| CONT         | 重新启动/如果在停止状态则重新启动，否则忽略 |
| PWR          | 忽略/在某些系统中会离开                     |
| WINCH        | 忽略                                        |
| CHLD         | 忽略                                        |
| ABRT 6       | 核心                                        |
| FPE 8        | 核心                                        |
| ILL 4        | 核心                                        |
| QUIT 3       | 核心                                        |
| SEGV 11      | 核心                                        |
| TRAP 5       | 核心                                        |
| SYS          | 核心/或许尚未实作                           |
| EMT          | 核心/或许尚未实作                           |
| BUS          | 核心/核心失败                               |
| XCPU         | 核心/核心失败                               |
| XFSZ         | 核心/核心失败                               |

### 实例

停止所有在 PTY 装置上的程序

```
skill -KILL -v pts/*
```

停止三个使用者 user1、user2、user3

```
skill -STOP user1 user2 user3
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)