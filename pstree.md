# Linux pstree 命令

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)

Linux pstree 命令将所有行程以树状图显示，树状图将会以 pid (如果有指定) 或是以 init 这个基本行程为根 (root)，如果有指定使用者 id，则树状图会只显示该使用者所拥有的行程。

使用权限：所有使用者。

### 语法

```
pstree [-a] [-c] [-h|-Hpid] [-l] [-n] [-p] [-u] [-G|-U] [pid|user]
```

或

```
pstree -V
```

**参数说明**：

- -a 显示该行程的完整指令及参数, 如果是被记忆体置换出去的行程则会加上括号
- -c 如果有重覆的行程名, 则分开列出（预设值是会在前面加上 *）

### 实例

显示进程的关系

```
[root@mobasv ~]# pstree
systemd─┬─BattleServer───41*[{BattleServer}]
        ├─BattleServerMgr───35*[{BattleServerMgr}]
        ├─DBServer───40*[{DBServer}]
        ├─DispatcherServe───35*[{DispatcherServe}]
        ├─GameServer───35*[{GameServer}]
        ├─LocalPublicServ───35*[{LocalPublicServ}]
        ├─LoginServer───40*[{LoginServer}]
        ├─MatchServer───35*[{MatchServer}]
        ├─NetworkManager───2*[{NetworkManager}]
        ├─TransferServer───35*[{TransferServer}]
        ├─VGAuthService
        ├─agetty
        ├─auditd───{auditd}
        ├─crond
        ├─dbus-daemon
        ├─dockerd-current─┬─docker-containe─┬─docker-containe─┬─mysqld───61*[{mysqld}]
        │                 │                 │                 └─9*[{docker-containe}]
        │                 │                 └─39*[{docker-containe}]
        │                 ├─docker-proxy-cu───7*[{docker-proxy-cu}]
        │                 └─42*[{dockerd-current}]
        ├─irqbalance
        ├─lvmetad
        ├─master─┬─pickup
        │        └─qmgr
        ├─polkitd───6*[{polkitd}]
        ├─rsyslogd───2*[{rsyslogd}]
        ├─sshd─┬─2*[sshd───sshd───bash]
        │      ├─sshd───sshd───bash───su───bash───pstree
        │      └─sshd───bash───man───less
        ├─systemd-journal
        ├─systemd-logind
        ├─systemd-udevd
        ├─tuned───4*[{tuned}]
        └─vmtoolsd───{vmtoolsd}
```

特别表明在运行的进程

```
[root@mobasv ~]# pstree -apnh //显示进程间的关系
systemd,1 --switched-root --system --deserialize 22
  ├─systemd-journal,685
  ├─lvmetad,712 -f
  ├─systemd-udevd,716
  ├─auditd,899
  │   └─{auditd},900
  ├─polkitd,922 --no-debug
  │   ├─{polkitd},936
  │   ├─{polkitd},937
  │   ├─{polkitd},938
  │   ├─{polkitd},941
  │   ├─{polkitd},945
  │   └─{polkitd},949
  ├─irqbalance,923 --foreground
  ├─VGAuthService,924 -s
  ├─vmtoolsd,925
  │   └─{vmtoolsd},952
  ├─dbus-daemon,928 --system --address=systemd: --nofork --nopidfile --systemd-activation
  ├─NetworkManager,939 --no-daemon
  │   ├─{NetworkManager},955
  │   └─{NetworkManager},957
  ├─systemd-logind,940
  ├─crond,944 -n
  ├─agetty,948 --noclear tty1 linux
  ├─sshd,1174 -D
  │   ├─sshd,756
  │   │   └─sshd,759
  │   │       └─bash,760
  │   ├─sshd,1850
  │   │   └─sshd,1853
  │   │       └─bash,1854
  │   ├─sshd,2006
  │   │   └─sshd,2009
  │   │       └─bash,2010
  │   │           └─su,6163 -
  │   │               └─bash,6170
  │   │                   └─pstree,6541 -apnh
  │   └─sshd,16446
  │       └─bash,16461
  │           └─man,27263 sscanf
  │               └─less,27283 -s
  ├─tuned,1175 -Es /usr/sbin/tuned -l -P
  │   ├─{tuned},1419
  │   ├─{tuned},1420
  │   ├─{tuned},1422
  │   └─{tuned},1423
  ├─rsyslogd,1177 -n
  │   ├─{rsyslogd},1180
  │   └─{rsyslogd},1181
  ├─master,1259 -w
  │   ├─qmgr,1261 -l -t unix -u
  │   └─pickup,11811 -l -t unix -u
  ├─DispatcherServe,3877 debug -d -c /data/xmoba//bin/config/template/DispatcherServer/config.xml --system-snet-ip 10.4.1.196 --dispatcher-server-ip 10.4.1.196
  │   ├─{DispatcherServe},3879
  │   ├─{DispatcherServe},3880
  │   ├─{DispatcherServe},3881
  │   ├─{DispatcherServe},3882
  │   ├─{DispatcherServe},3883
  │   ├─{DispatcherServe},3884
  │   ├─{DispatcherServe},3885
  │   ├─{DispatcherServe},3886
  │   ├─{DispatcherServe},3887
  │   ├─{DispatcherServe},3888
  │   ├─{DispatcherServe},3889
  │   ├─{DispatcherServe},3890
  │   ├─{DispatcherServe},3891
  │   ├─{DispatcherServe},3892
  │   ├─{DispatcherServe},3893
  │   ├─{DispatcherServe},3894
  │   ├─{DispatcherServe},3895
  │   ├─{DispatcherServe},3896
  │   ├─{DispatcherServe},3897
  │   ├─{DispatcherServe},3898
  │   ├─{DispatcherServe},3899
  │   ├─{DispatcherServe},3900
  │   ├─{DispatcherServe},3901
  │   ├─{DispatcherServe},3902
  │   ├─{DispatcherServe},3903
  │   ├─{DispatcherServe},3904
  │   ├─{DispatcherServe},3905
  │   ├─{DispatcherServe},3906
  │   ├─{DispatcherServe},3907
  │   ├─{DispatcherServe},3908
  │   ├─{DispatcherServe},3909
  │   ├─{DispatcherServe},3910
  │   ├─{DispatcherServe},3911
  │   ├─{DispatcherServe},3912
  │   └─{DispatcherServe},3913
......
```

同时显示用户名称

```
[root@mobasv ~]# pstree -u //显示用户名称
systemd─┬─BattleServer(dev)───41*[{BattleServer}]
        ├─BattleServerMgr(dev)───35*[{BattleServerMgr}]
        ├─DBServer(dev)───40*[{DBServer}]
        ├─DispatcherServe(dev)───35*[{DispatcherServe}]
        ├─GameServer(dev)───35*[{GameServer}]
        ├─LocalPublicServ(dev)───35*[{LocalPublicServ}]
        ├─LoginServer(dev)───40*[{LoginServer}]
        ├─MatchServer(dev)───35*[{MatchServer}]
        ├─NetworkManager───2*[{NetworkManager}]
        ├─TransferServer(dev)───35*[{TransferServer}]
        ├─VGAuthService
        ├─agetty
        ├─auditd───{auditd}
        ├─crond
        ├─dbus-daemon(dbus)
        ├─dockerd-current─┬─docker-containe─┬─docker-containe─┬─mysqld(polkitd)───61*[{mysqld}]
        │                 │                 │                 └─9*[{docker-containe}]
        │                 │                 └─39*[{docker-containe}]
        │                 ├─docker-proxy-cu───7*[{docker-proxy-cu}]
        │                 └─42*[{dockerd-current}]
        ├─irqbalance
        ├─lvmetad
        ├─master─┬─pickup(postfix)
        │        └─qmgr(postfix)
        ├─polkitd(polkitd)───6*[{polkitd}]
        ├─rsyslogd───2*[{rsyslogd}]
        ├─sshd─┬─2*[sshd───sshd(dev)───bash]
        │      ├─sshd───sshd(dev)───bash───su(root)───bash───pstree
        │      └─sshd───bash───man───less
        ├─systemd-journal
        ├─systemd-logind
        ├─systemd-udevd
        ├─tuned───4*[{tuned}]
        └─vmtoolsd───{vmtoolsd}

```

返回 [Linux 命令大全](https://ahuang007.github.com/Linux-Command)