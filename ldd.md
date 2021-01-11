# Linux ldd 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

**ldd**的作用是打印可执行档依赖的共享库文件。它是glibc的一部分

**ldd**本身不是一个程序，而仅是一个shell脚本：

```
[dev@mobasv log]$ which ldd
/bin/ldd
```

ldd 帮助命令

```
[dev@mobasv log]$ ldd --help
Usage: ldd [OPTION]... FILE...
      --help              print this help and exit
      --version           print version information and exit
  -d, --data-relocs       process data relocations
  -r, --function-relocs   process data and function relocations
  -u, --unused            print unused direct dependencies
  -v, --verbose           print all information

For bug reporting instructions, please see:
<http://www.gnu.org/software/libc/bugs.html>.
```

ldd 查看 GameServer 依赖的共享库文件

```
[dev@mobasv GameServer]$ ldd GameServer
	linux-vdso.so.1 =>  (0x00007ffde67f5000)
	libpthread.so.0 => /lib64/libpthread.so.0 (0x00007f957b5cf000)
	libcurl.so.4 => /usr/local/lib/libcurl.so.4 (0x00007f957b351000)
	libz.so.1 => /lib64/libz.so.1 (0x00007f957b13b000)
	libstdc++.so.6 => /usr/local/lib64/libstdc++.so.6 (0x00007f957ad6e000)
	libm.so.6 => /lib64/libm.so.6 (0x00007f957aa6c000)
	libgcc_s.so.1 => /usr/local/lib64/libgcc_s.so.1 (0x00007f957a854000)
	libc.so.6 => /lib64/libc.so.6 (0x00007f957a486000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f957b7eb000)
	libssl.so.10 => /lib64/libssl.so.10 (0x00007f957a214000)
	libcrypto.so.10 => /lib64/libcrypto.so.10 (0x00007f9579db1000)
	libgssapi_krb5.so.2 => /lib64/libgssapi_krb5.so.2 (0x00007f9579b64000)
	libkrb5.so.3 => /lib64/libkrb5.so.3 (0x00007f957987b000)
	libcom_err.so.2 => /lib64/libcom_err.so.2 (0x00007f9579677000)
	libk5crypto.so.3 => /lib64/libk5crypto.so.3 (0x00007f9579444000)
	libdl.so.2 => /lib64/libdl.so.2 (0x00007f9579240000)
	libkrb5support.so.0 => /lib64/libkrb5support.so.0 (0x00007f9579030000)
	libkeyutils.so.1 => /lib64/libkeyutils.so.1 (0x00007f9578e2c000)
	libresolv.so.2 => /lib64/libresolv.so.2 (0x00007f9578c12000)
	libselinux.so.1 => /lib64/libselinux.so.1 (0x00007f95789eb000)
	libpcre.so.1 => /lib64/libpcre.so.1 (0x00007f9578789000)
```



返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)