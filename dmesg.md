# Linux dmesg 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

`dmesg = diagnostic message`

Linux dmesg命令用于显示开机信息。

kernel会将开机信息存储在ring buffer中。您若是开机时来不及查看信息，可利用dmesg来查看。开机信息亦保存在/var/log目录中，名称为dmesg的文件里。

### 语法

```
dmesg [-cn][-s <缓冲区大小>]
```

**参数说明**：

- -c 　显示信息后，清除ring buffer中的内容。
- -s<缓冲区大小> 　预设置为8196，刚好等于ring buffer的大小。
- -n 　设置记录信息的层级。

### 实例

显示开机信息

```
[huanglijun@localhost test]$ dmesg | less # 从头开始看
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.10.0-514.el7.x86_64 (builder@kbuilder.dev.centos.org) (gcc version 4.8.5 20150623 (Red Hat 4.8.5-11) (GCC) ) #1 SMP Tue Nov 22 16:42:41 UTC 2016
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.10.0-514.el7.x86_64 root=/dev/mapper/cl-root ro crashkernel=auto rd.lvm.lv=cl/root rd.lvm.lv=cl/swap rhgb quiet LANG=zh_CN.UTF-8
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007fc54fff] usable
[    0.000000] BIOS-e820: [mem 0x000000007fc55000-0x000000007fc55fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000007fc56000-0x000000007fc56fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000007fc57000-0x000000008c8f6fff] usable
[    0.000000] BIOS-e820: [mem 0x000000008c8f7000-0x000000008e1b2fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008e1b3000-0x000000008e20cfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000008e20d000-0x000000008e5fefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000008e5ff000-0x000000008f7a1fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000008f7a2000-0x000000008f7fffff] usable
[    0.000000] BIOS-e820: [mem 0x000000008f800000-0x000000008fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe000000-0x00000000fe010fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000086effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] e820: update [mem 0x7f54c018-0x7f56bc57] usable ==> usable
[    0.000000] e820: update [mem 0x7f53b018-0x7f54be57] usable ==> usable
[    0.000000] extended physical RAM map:
[    0.000000] reserve setup_data: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] reserve setup_data: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000059000-0x000000000009efff] usable
[    0.000000] reserve setup_data: [mem 0x000000000009f000-0x00000000000fffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000100000-0x000000007f53b017] usable
[    0.000000] reserve setup_data: [mem 0x000000007f53b018-0x000000007f54be57] usable
[    0.000000] reserve setup_data: [mem 0x000000007f54be58-0x000000007f54c017] usable
[    0.000000] reserve setup_data: [mem 0x000000007f54c018-0x000000007f56bc57] usable
[    0.000000] reserve setup_data: [mem 0x000000007f56bc58-0x000000007fc54fff] usable
[    0.000000] reserve setup_data: [mem 0x000000007fc55000-0x000000007fc55fff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x000000007fc56000-0x000000007fc56fff] reserved

#保存到文件
[huanglijun@localhost test]$ dmesg > boot.txt
```



返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)