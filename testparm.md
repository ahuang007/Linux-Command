# Linux testparm 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux testparm 命令用于测试 Samba 的设置是否正确无误。

执行 testparm(test parameter) 指令可以简单测试 Samba 的配置文件，假如测试结果无误，Samba 常驻服务就能正确载入该设置值，但并不保证其后的操作如预期般一切正常。

### 语法

```
testparm [-s][配置文件][<主机名称><IP地址>]
```

**参数说明**：

- -s 不显示提示符号等待用户按下Enter键，就直接列出Samba服务定义信息。

### 实例

查看Ssmba配置

```
[root@iZwz9i5ym7nzoefwpmoszjZ ~]# testparm
Registered MSG_REQ_POOL_USAGE
Registered MSG_REQ_DMALLOC_MARK and LOG_CHANGED
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[root]"
Loaded services file OK.
WARNING: The 'netbios name' is too long (max. 15 chars).

Server role: ROLE_STANDALONE

Press enter to see a dump of your service definition
Global parameters
# Global parameters
[global]
	printcap name = cups
	security = USER
	smb ports = 1315 1314
	workgroup = SAMBA
	idmap config * : backend = tdb
	cups options = raw


[homes]
	browseable = No
	comment = Home Directories
	inherit acls = Yes
	read only = No
	valid users = %S %D%w%S


[printers]
	browseable = No
	comment = All Printers
	create mask = 0600
	path = /var/tmp
	printable = Yes


[print$]
	comment = Printer Drivers
	create mask = 0664
	directory mask = 0775
	force group = @printadmin
	path = /var/lib/samba/drivers
	write list = @printadmin root


[root]
	comment = root
	create mask = 0777
	directory mask = 0777
	guest ok = Yes
	path = /home
	read only = No
```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)