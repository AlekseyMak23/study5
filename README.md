Домашнее задание "Vagrant стенд для NFS"

1. Создаем виртуальные машины

 - Создаем VagrantFile с указанными в задании настройками (2 виртуальные машины - сервер nfss и клиент nfsc);
 - Включаем вм - vagrant up;

2. Настраиваем сервер NFS

 - Подключаемся к серверу - vagrant ssh nfss, переходим в root - sudo -i

 - Доустановим утилиты:
~~~
[root@nfss ~]# yum install nfs-utils
Failed to set locale, defaulting to C
Loaded plugins: fastestmirror
Determining fastest mirrors
 * base: centos.intergenia.de
 * extras: ftp.fau.de
 * updates: centos.intergenia.de

base                                                                                                                                                                                                                  | 3.6 kB  00:00:00     

extras                                                                                                                                                                                                                | 2.9 kB  00:00:00     

updates                                                                                                                                                                                                               | 2.9 kB  00:00:00     

(2/4): base/7/x86_64/primary_db                                                                          0% [                                                                                              ]  0.0 B/s |    0 B  --:--:-- ETA 

(1/4): extras/7/x86_64/primary_db                                                                                                                                                                                     | 249 kB  00:00:00     

(2/4): base/7/x86_64/group_gz                                                                                                                                                                                         | 153 kB  00:00:00     

(4/4): updates/7/x86_64/primary_db                                                                       5% [=====                                                                                         ]  0.0 B/s | 1.6 MB  --:--:-- ETA 

(4/4): updates/7/x86_64/primary_db                                                                      12% [============                                                                                  ] 3.1 MB/s | 3.5 MB  00:00:07 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      21% [====================                                                                          ] 3.4 MB/s | 5.9 MB  00:00:06 ETA 

(3/4): base/7/x86_64/primary_db                                                                         30% [============================                                                                  ] 3.7 MB/s | 8.2 MB  00:00:05 ETA 

(3/4): base/7/x86_64/primary_db                                                                         38% [====================================                                                          ] 3.9 MB/s |  11 MB  00:00:04 ETA 

(3/4): base/7/x86_64/primary_db                                                                         47% [============================================-                                                 ] 4.2 MB/s |  13 MB  00:00:03 ETA 

(3/4): base/7/x86_64/primary_db                                                                         56% [=====================================================                                         ] 4.4 MB/s |  15 MB  00:00:02 ETA 

(3/4): base/7/x86_64/primary_db                                                                                                                                                                                       | 6.1 MB  00:00:02     

(4/4): updates/7/x86_64/primary_db                                                                      69% [=================================================================                             ] 4.6 MB/s |  19 MB  00:00:01 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      74% [======================================================================                        ] 4.6 MB/s |  20 MB  00:00:01 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      79% [===========================================================================                   ] 4.6 MB/s |  22 MB  00:00:01 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      84% [===============================================================================               ] 4.5 MB/s |  23 MB  00:00:00 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      89% [===================================================================================-          ] 4.5 MB/s |  24 MB  00:00:00 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      94% [========================================================================================-     ] 4.5 MB/s |  26 MB  00:00:00 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      99% [=============================================================================================-] 4.5 MB/s |  27 MB  00:00:00 ETA 

(4/4): updates/7/x86_64/primary_db                                                                                                                                                                                    |  21 MB  00:00:05     
Resolving Dependencies
--> Running transaction check
---> Package nfs-utils.x86_64 1:1.3.0-0.66.el7 will be updated
---> Package nfs-utils.x86_64 1:1.3.0-0.68.el7.2 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

=============================================================================================================================================================================================================================================
 Package                                                 Arch                                                 Version                                                            Repository                                             Size
=============================================================================================================================================================================================================================================
Updating:
 nfs-utils                                               x86_64                                               1:1.3.0-0.68.el7.2                                                 updates                                               413 k

Transaction Summary
=============================================================================================================================================================================================================================================
Upgrade  1 Package

Total download size: 413 k
Is this ok [y/d/N]: y
Downloading packages:
No Presto metadata available for updates
warning: /var/cache/yum/x86_64/7/updates/packages/nfs-utils-1.3.0-0.68.el7.2.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID f4a80eb5: NOKEY
Public key for nfs-utils-1.3.0-0.68.el7.2.x86_64.rpm is not installed

nfs-utils-1.3.0-0.68.el7.2.x86_64.rpm                                                                                                                                                                                 | 413 kB  00:00:00     
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Importing GPG key 0xF4A80EB5:
 Userid     : "CentOS-7 Key (CentOS 7 Official Signing Key) <security@centos.org>"
 Fingerprint: 6341 ab27 53d7 8a78 a7c2 7bb1 24c6 a8a7 f4a8 0eb5
 Package    : centos-release-7-8.2003.0.el7.centos.x86_64 (@anaconda)
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Is this ok [y/N]: y
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction

  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [                                                                                                                                                                                   ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [##########                                                                                                                                                                         ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [###################                                                                                                                                                                ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [##############################                                                                                                                                                     ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [###################################                                                                                                                                                ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [############################################                                                                                                                                       ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [##################################################                                                                                                                                 ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#########################################################                                                                                                                          ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [####################################################################                                                                                                               ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#####################################################################                                                                                                              ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [############################################################################                                                                                                       ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [####################################################################################                                                                                               ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#####################################################################################                                                                                              ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [###########################################################################################                                                                                        ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [##############################################################################################                                                                                     ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#########################################################################################################                                                                          ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#############################################################################################################                                                                      ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [######################################################################################################################                                                             ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [################################################################################################################################                                                   ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#########################################################################################################################################                                          ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [###########################################################################################################################################                                        ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [################################################################################################################################################                                   ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [####################################################################################################################################################                               ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [########################################################################################################################################################                           ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#################################################################################################################################################################                  ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [##################################################################################################################################################################                 ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [####################################################################################################################################################################               ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [######################################################################################################################################################################             ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [########################################################################################################################################################################           ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [##########################################################################################################################################################################         ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [###########################################################################################################################################################################        ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#############################################################################################################################################################################      ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [###############################################################################################################################################################################    ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#################################################################################################################################################################################  ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64                                                                                                                                                                                       1/2 

  Cleanup    : 1:nfs-utils-1.3.0-0.66.el7.x86_64                                                                                                                                                                                         2/2 

  Verifying  : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64                                                                                                                                                                                       1/2 

  Verifying  : 1:nfs-utils-1.3.0-0.66.el7.x86_64                                                                                                                                                                                         2/2 

Updated:
  nfs-utils.x86_64 1:1.3.0-0.68.el7.2                                                                                                                                                                                                        

Complete!
~~~

 - Включаем файрвол и проверяем работу:
~~~
[root@nfss ~]# systemctl enable firewalld --now 
Created symlink from /etc/systemd/system/dbus-org.fedoraproject.FirewallD1.service to /usr/lib/systemd/system/firewalld.service.
Created symlink from /etc/systemd/system/multi-user.target.wants/firewalld.service to /usr/lib/systemd/system/firewalld.service.

[root@nfss ~]# iptables-save
# Generated by iptables-save v1.4.21 on Wed May 24 06:17:33 2023
*nat
:PREROUTING ACCEPT [1:84]
:INPUT ACCEPT [1:84]
:OUTPUT ACCEPT [4:304]
:POSTROUTING ACCEPT [4:304]
:OUTPUT_direct - [0:0]
:POSTROUTING_ZONES - [0:0]
:POSTROUTING_ZONES_SOURCE - [0:0]
:POSTROUTING_direct - [0:0]
:POST_public - [0:0]
:POST_public_allow - [0:0]
:POST_public_deny - [0:0]
:POST_public_log - [0:0]
:PREROUTING_ZONES - [0:0]
:PREROUTING_ZONES_SOURCE - [0:0]
:PREROUTING_direct - [0:0]
:PRE_public - [0:0]
:PRE_public_allow - [0:0]
:PRE_public_deny - [0:0]
:PRE_public_log - [0:0]
-A PREROUTING -j PREROUTING_direct
-A PREROUTING -j PREROUTING_ZONES_SOURCE
-A PREROUTING -j PREROUTING_ZONES
-A OUTPUT -j OUTPUT_direct
-A POSTROUTING -j POSTROUTING_direct
-A POSTROUTING -j POSTROUTING_ZONES_SOURCE
-A POSTROUTING -j POSTROUTING_ZONES
-A POSTROUTING_ZONES -o eth1 -g POST_public
-A POSTROUTING_ZONES -o eth0 -g POST_public
-A POSTROUTING_ZONES -g POST_public
-A POST_public -j POST_public_log
-A POST_public -j POST_public_deny
-A POST_public -j POST_public_allow
-A PREROUTING_ZONES -i eth1 -g PRE_public
-A PREROUTING_ZONES -i eth0 -g PRE_public
-A PREROUTING_ZONES -g PRE_public
-A PRE_public -j PRE_public_log
-A PRE_public -j PRE_public_deny
-A PRE_public -j PRE_public_allow
COMMIT
# Completed on Wed May 24 06:17:33 2023
# Generated by iptables-save v1.4.21 on Wed May 24 06:17:33 2023
*mangle
:PREROUTING ACCEPT [38:2248]
:INPUT ACCEPT [38:2248]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [22:2176]
:POSTROUTING ACCEPT [22:2176]
:FORWARD_direct - [0:0]
:INPUT_direct - [0:0]
:OUTPUT_direct - [0:0]
:POSTROUTING_direct - [0:0]
:PREROUTING_ZONES - [0:0]
:PREROUTING_ZONES_SOURCE - [0:0]
:PREROUTING_direct - [0:0]
:PRE_public - [0:0]
:PRE_public_allow - [0:0]
:PRE_public_deny - [0:0]
:PRE_public_log - [0:0]
-A PREROUTING -j PREROUTING_direct
-A PREROUTING -j PREROUTING_ZONES_SOURCE
-A PREROUTING -j PREROUTING_ZONES
-A INPUT -j INPUT_direct
-A FORWARD -j FORWARD_direct
-A OUTPUT -j OUTPUT_direct
-A POSTROUTING -j POSTROUTING_direct
-A PREROUTING_ZONES -i eth1 -g PRE_public
-A PREROUTING_ZONES -i eth0 -g PRE_public
-A PREROUTING_ZONES -g PRE_public
-A PRE_public -j PRE_public_log
-A PRE_public -j PRE_public_deny
-A PRE_public -j PRE_public_allow
COMMIT
# Completed on Wed May 24 06:17:33 2023
# Generated by iptables-save v1.4.21 on Wed May 24 06:17:33 2023
*security
:INPUT ACCEPT [38:2248]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [22:2176]
:FORWARD_direct - [0:0]
:INPUT_direct - [0:0]
:OUTPUT_direct - [0:0]
-A INPUT -j INPUT_direct
-A FORWARD -j FORWARD_direct
-A OUTPUT -j OUTPUT_direct
COMMIT
# Completed on Wed May 24 06:17:33 2023
# Generated by iptables-save v1.4.21 on Wed May 24 06:17:33 2023
*raw
:PREROUTING ACCEPT [38:2248]
:OUTPUT ACCEPT [22:2176]
:OUTPUT_direct - [0:0]
:PREROUTING_ZONES - [0:0]
:PREROUTING_ZONES_SOURCE - [0:0]
:PREROUTING_direct - [0:0]
:PRE_public - [0:0]
:PRE_public_allow - [0:0]
:PRE_public_deny - [0:0]
:PRE_public_log - [0:0]
-A PREROUTING -j PREROUTING_direct
-A PREROUTING -j PREROUTING_ZONES_SOURCE
-A PREROUTING -j PREROUTING_ZONES
-A OUTPUT -j OUTPUT_direct
-A PREROUTING_ZONES -i eth1 -g PRE_public
-A PREROUTING_ZONES -i eth0 -g PRE_public
-A PREROUTING_ZONES -g PRE_public
-A PRE_public -j PRE_public_log
-A PRE_public -j PRE_public_deny
-A PRE_public -j PRE_public_allow
COMMIT
# Completed on Wed May 24 06:17:33 2023
# Generated by iptables-save v1.4.21 on Wed May 24 06:17:33 2023
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [22:2176]
:FORWARD_IN_ZONES - [0:0]
:FORWARD_IN_ZONES_SOURCE - [0:0]
:FORWARD_OUT_ZONES - [0:0]
:FORWARD_OUT_ZONES_SOURCE - [0:0]
:FORWARD_direct - [0:0]
:FWDI_public - [0:0]
:FWDI_public_allow - [0:0]
:FWDI_public_deny - [0:0]
:FWDI_public_log - [0:0]
:FWDO_public - [0:0]
:FWDO_public_allow - [0:0]
:FWDO_public_deny - [0:0]
:FWDO_public_log - [0:0]
:INPUT_ZONES - [0:0]
:INPUT_ZONES_SOURCE - [0:0]
:INPUT_direct - [0:0]
:IN_public - [0:0]
:IN_public_allow - [0:0]
:IN_public_deny - [0:0]
:IN_public_log - [0:0]
:OUTPUT_direct - [0:0]
-A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -j INPUT_direct
-A INPUT -j INPUT_ZONES_SOURCE
-A INPUT -j INPUT_ZONES
-A INPUT -m conntrack --ctstate INVALID -j DROP
-A INPUT -j REJECT --reject-with icmp-host-prohibited
-A FORWARD -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -i lo -j ACCEPT
-A FORWARD -j FORWARD_direct
-A FORWARD -j FORWARD_IN_ZONES_SOURCE
-A FORWARD -j FORWARD_IN_ZONES
-A FORWARD -j FORWARD_OUT_ZONES_SOURCE
-A FORWARD -j FORWARD_OUT_ZONES
-A FORWARD -m conntrack --ctstate INVALID -j DROP
-A FORWARD -j REJECT --reject-with icmp-host-prohibited
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -j OUTPUT_direct
-A FORWARD_IN_ZONES -i eth1 -g FWDI_public
-A FORWARD_IN_ZONES -i eth0 -g FWDI_public
-A FORWARD_IN_ZONES -g FWDI_public
-A FORWARD_OUT_ZONES -o eth1 -g FWDO_public
-A FORWARD_OUT_ZONES -o eth0 -g FWDO_public
-A FORWARD_OUT_ZONES -g FWDO_public
-A FWDI_public -j FWDI_public_log
-A FWDI_public -j FWDI_public_deny
-A FWDI_public -j FWDI_public_allow
-A FWDI_public -p icmp -j ACCEPT
-A FWDO_public -j FWDO_public_log
-A FWDO_public -j FWDO_public_deny
-A FWDO_public -j FWDO_public_allow
-A INPUT_ZONES -i eth1 -g IN_public
-A INPUT_ZONES -i eth0 -g IN_public
-A INPUT_ZONES -g IN_public
-A IN_public -j IN_public_log
-A IN_public -j IN_public_deny
-A IN_public -j IN_public_allow
-A IN_public -p icmp -j ACCEPT
-A IN_public_allow -p tcp -m tcp --dport 22 -m conntrack --ctstate NEW,UNTRACKED -j ACCEPT
COMMIT
# Completed on Wed May 24 06:17:33 2023
~~~

 - Разрешаем в firewall доступ к сервисам NFS:
~~~
[root@nfss ~]# firewall-cmd --add-service="nfs3" \
> --add-service="rpc-bind" \
> --add-service="mountd" \
> --permanent 
success
[root@nfss ~]# firewall-cmd --reload
success
~~~

 - Включаем сервер NFS:
~~~
[root@nfss ~]# systemctl enable nfs --now 
Created symlink from /etc/systemd/system/multi-user.target.wants/nfs-server.service to /usr/lib/systemd/system/nfs-server.service.
~~~

 - Проверяем наличие слушаемых портов:
~~~
[root@nfss ~]# ss -tnplu 
Netid State      Recv-Q Send-Q                                                                       Local Address:Port                                                                                      Peer Address:Port              
udp   UNCONN     0      0                                                                                        *:930                                                                                                  *:*                   users:(("rpcbind",pid=332,fd=7))
udp   UNCONN     0      0                                                                                        *:2049                                                                                                 *:*                  
udp   UNCONN     0      0                                                                                127.0.0.1:834                                                                                                  *:*                   users:(("rpc.statd",pid=3196,fd=12))
udp   UNCONN     0      0                                                                                127.0.0.1:323                                                                                                  *:*                   users:(("chronyd",pid=357,fd=5))
udp   UNCONN     0      0                                                                                        *:68                                                                                                   *:*                   users:(("dhclient",pid=2478,fd=6))
udp   UNCONN     0      0                                                                                        *:20048                                                                                                *:*                   users:(("rpc.mountd",pid=3202,fd=7))
udp   UNCONN     0      0                                                                                        *:36441                                                                                                *:*                  
udp   UNCONN     0      0                                                                                        *:47466                                                                                                *:*                   users:(("rpc.statd",pid=3196,fd=7))
udp   UNCONN     0      0                                                                                        *:111                                                                                                  *:*                   users:(("rpcbind",pid=332,fd=6))
udp   UNCONN     0      0                                                                                     [::]:930                                                                                               [::]:*                   users:(("rpcbind",pid=332,fd=10))
udp   UNCONN     0      0                                                                                     [::]:34303                                                                                             [::]:*                   users:(("rpc.statd",pid=3196,fd=9))
udp   UNCONN     0      0                                                                                     [::]:2049                                                                                              [::]:*                  
udp   UNCONN     0      0                                                                                    [::1]:323                                                                                               [::]:*                   users:(("chronyd",pid=357,fd=6))
udp   UNCONN     0      0                                                                                     [::]:20048                                                                                             [::]:*                   users:(("rpc.mountd",pid=3202,fd=9))
udp   UNCONN     0      0                                                                                     [::]:111                                                                                               [::]:*                   users:(("rpcbind",pid=332,fd=9))
udp   UNCONN     0      0                                                                                     [::]:34416                                                                                             [::]:*                  
tcp   LISTEN     0      64                                                                                       *:38987                                                                                                *:*                  
tcp   LISTEN     0      128                                                                                      *:111                                                                                                  *:*                   users:(("rpcbind",pid=332,fd=8))
tcp   LISTEN     0      128                                                                                      *:20048                                                                                                *:*                   users:(("rpc.mountd",pid=3202,fd=8))
tcp   LISTEN     0      128                                                                                      *:22                                                                                                   *:*                   users:(("sshd",pid=613,fd=3))
tcp   LISTEN     0      100                                                                              127.0.0.1:25                                                                                                   *:*                   users:(("master",pid=754,fd=13))
tcp   LISTEN     0      128                                                                                      *:34912                                                                                                *:*                   users:(("rpc.statd",pid=3196,fd=8))
tcp   LISTEN     0      64                                                                                       *:2049                                                                                                 *:*                  
tcp   LISTEN     0      128                                                                                   [::]:111                                                                                               [::]:*                   users:(("rpcbind",pid=332,fd=11))
tcp   LISTEN     0      128                                                                                   [::]:20048                                                                                             [::]:*                   users:(("rpc.mountd",pid=3202,fd=10))
tcp   LISTEN     0      128                                                                                   [::]:45748                                                                                             [::]:*                   users:(("rpc.statd",pid=3196,fd=10))
tcp   LISTEN     0      128                                                                                   [::]:22                                                                                                [::]:*                   users:(("sshd",pid=613,fd=4))
tcp   LISTEN     0      100                                                                                  [::1]:25                                                                                                [::]:*                   users:(("master",pid=754,fd=14))
tcp   LISTEN     0      64                                                                                    [::]:34497                                                                                             [::]:*                  
tcp   LISTEN     0      64                                                                                    [::]:2049                                                                                              [::]:*                  
~~~

 - Создаём и настраиваем директорию для экспорта, назначаем права:
~~~
[root@nfss ~]#  mkdir -p /srv/share/upload 
[root@nfss ~]# chown -R nfsnobody:nfsnobody /srv/share 
[root@nfss ~]# chmod 0777 /srv/share/upload 
~~~

 - Создаём в файле /etc/exports структуру для экспорта:
~~~
[root@nfss ~]# cat << EOF > /etc/exports 
> /srv/share 192.168.56.11/32(rw,sync,root_squash) 
> EOF
~~~

 - Экспортируем ранее созданную директорию:
~~~
[root@nfss ~]# exportfs -r
~~~

 - Проверяем экспортированную директорию:
~~~
[root@nfss ~]# exportfs -s
/srv/share  192.168.56.11/32(sync,wdelay,hide,no_subtree_check,sec=sys,rw,secure,root_squash,no_all_squash)
~~~


3. Настраиваем клиент NFS

 - Подключаемся к клиенту - vagrant ssh nfsc, переходим в root - sudo -i

 - Доустановим утилиты:

~~~
[root@nfsc ~]# yum install nfs-utils
Failed to set locale, defaulting to C
Loaded plugins: fastestmirror
Determining fastest mirrors
 * base: ftp.plusline.net
 * extras: ftp.plusline.net
 * updates: ftp.plusline.net

base                                                                                                                                                                                                                  | 3.6 kB  00:00:00     

extras                                                                                                                                                                                                                | 2.9 kB  00:00:00     

updates                                                                                                                                                                                                               | 2.9 kB  00:00:00     

(2/4): base/7/x86_64/primary_db                                                                          0% [                                                                                              ]  0.0 B/s |    0 B  --:--:-- ETA 

(1/4): base/7/x86_64/group_gz                                                                                                                                                                                         | 153 kB  00:00:00     

(2/4): extras/7/x86_64/primary_db                                                                                                                                                                                     | 249 kB  00:00:00     

(4/4): updates/7/x86_64/primary_db                                                                       2% [==                                                                                            ]  0.0 B/s | 691 kB  --:--:-- ETA 

(4/4): updates/7/x86_64/primary_db                                                                       5% [=====                                                                                         ] 1.3 MB/s | 1.5 MB  00:00:20 ETA 

(4/4): updates/7/x86_64/primary_db                                                                       9% [=========                                                                                     ] 1.4 MB/s | 2.7 MB  00:00:17 ETA 

(3/4): base/7/x86_64/primary_db                                                                         14% [=============                                                                                 ] 1.6 MB/s | 3.9 MB  00:00:14 ETA 

(3/4): base/7/x86_64/primary_db                                                                         19% [=================-                                                                            ] 1.7 MB/s | 5.2 MB  00:00:12 ETA 

(3/4): base/7/x86_64/primary_db                                                                         24% [======================-                                                                       ] 1.9 MB/s | 6.6 MB  00:00:10 ETA 

(3/4): base/7/x86_64/primary_db                                                                         29% [============================                                                                  ] 2.1 MB/s | 8.2 MB  00:00:09 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      35% [=================================-                                                            ] 2.3 MB/s | 9.8 MB  00:00:07 ETA 

(3/4): base/7/x86_64/primary_db                                                                                                                                                                                       | 6.1 MB  00:00:03     

(4/4): updates/7/x86_64/primary_db                                                                      43% [=========================================                                                     ] 2.6 MB/s |  12 MB  00:00:05 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      46% [===========================================-                                                  ] 2.6 MB/s |  13 MB  00:00:05 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      50% [===============================================                                               ] 2.6 MB/s |  14 MB  00:00:05 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      53% [==================================================                                            ] 2.6 MB/s |  15 MB  00:00:04 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      57% [=====================================================-                                        ] 2.7 MB/s |  16 MB  00:00:04 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      61% [=========================================================-                                    ] 2.7 MB/s |  17 MB  00:00:03 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      65% [=============================================================-                                ] 2.8 MB/s |  18 MB  00:00:03 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      70% [=================================================================-                            ] 2.9 MB/s |  19 MB  00:00:02 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      74% [=====================================================================-                        ] 2.9 MB/s |  20 MB  00:00:02 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      79% [==========================================================================                    ] 3.0 MB/s |  22 MB  00:00:01 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      83% [==============================================================================-               ] 3.1 MB/s |  23 MB  00:00:01 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      88% [===================================================================================           ] 3.1 MB/s |  24 MB  00:00:00 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      93% [========================================================================================      ] 3.2 MB/s |  26 MB  00:00:00 ETA 

(4/4): updates/7/x86_64/primary_db                                                                      98% [============================================================================================- ] 3.3 MB/s |  27 MB  00:00:00 ETA 

(4/4): updates/7/x86_64/primary_db                                                                                                                                                                                    |  21 MB  00:00:07     
Resolving Dependencies
--> Running transaction check
---> Package nfs-utils.x86_64 1:1.3.0-0.66.el7 will be updated
---> Package nfs-utils.x86_64 1:1.3.0-0.68.el7.2 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

=============================================================================================================================================================================================================================================
 Package                                                 Arch                                                 Version                                                            Repository                                             Size
=============================================================================================================================================================================================================================================
Updating:
 nfs-utils                                               x86_64                                               1:1.3.0-0.68.el7.2                                                 updates                                               413 k

Transaction Summary
=============================================================================================================================================================================================================================================
Upgrade  1 Package

Total download size: 413 k
Is this ok [y/d/N]: y
Downloading packages:
No Presto metadata available for updates
warning: /var/cache/yum/x86_64/7/updates/packages/nfs-utils-1.3.0-0.68.el7.2.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID f4a80eb5: NOKEY
Public key for nfs-utils-1.3.0-0.68.el7.2.x86_64.rpm is not installed

nfs-utils-1.3.0-0.68.el7.2.x86_64.rpm                                                                                                                                                                                 | 413 kB  00:00:00     
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Importing GPG key 0xF4A80EB5:
 Userid     : "CentOS-7 Key (CentOS 7 Official Signing Key) <security@centos.org>"
 Fingerprint: 6341 ab27 53d7 8a78 a7c2 7bb1 24c6 a8a7 f4a8 0eb5
 Package    : centos-release-7-8.2003.0.el7.centos.x86_64 (@anaconda)
 From       : /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
Is this ok [y/N]: y
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction

  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [                                                                                                                                                                                   ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [##########                                                                                                                                                                         ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [###################                                                                                                                                                                ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [##############################                                                                                                                                                     ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [###################################                                                                                                                                                ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [############################################                                                                                                                                       ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [##################################################                                                                                                                                 ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#########################################################                                                                                                                          ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [####################################################################                                                                                                               ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#####################################################################                                                                                                              ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [############################################################################                                                                                                       ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [####################################################################################                                                                                               ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#####################################################################################                                                                                              ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [###########################################################################################                                                                                        ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [##############################################################################################                                                                                     ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#########################################################################################################                                                                          ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#############################################################################################################                                                                      ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [######################################################################################################################                                                             ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [################################################################################################################################                                                   ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#########################################################################################################################################                                          ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [###########################################################################################################################################                                        ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [################################################################################################################################################                                   ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [####################################################################################################################################################                               ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [########################################################################################################################################################                           ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#################################################################################################################################################################                  ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [##################################################################################################################################################################                 ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [####################################################################################################################################################################               ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [######################################################################################################################################################################             ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [########################################################################################################################################################################           ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [##########################################################################################################################################################################         ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [###########################################################################################################################################################################        ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#############################################################################################################################################################################      ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [###############################################################################################################################################################################    ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64 [#################################################################################################################################################################################  ] 1/2
  Updating   : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64                                                                                                                                                                                       1/2 

  Cleanup    : 1:nfs-utils-1.3.0-0.66.el7.x86_64                                                                                                                                                                                         2/2 

  Verifying  : 1:nfs-utils-1.3.0-0.68.el7.2.x86_64                                                                                                                                                                                       1/2 

  Verifying  : 1:nfs-utils-1.3.0-0.66.el7.x86_64                                                                                                                                                                                         2/2 

Updated:
  nfs-utils.x86_64 1:1.3.0-0.68.el7.2                                                                                                                                                                                                        

Complete!
~~~

 - Включаем firewall и проверяем, что он работает:
~~~
[root@nfsc ~]# systemctl enable firewalld --now 
Created symlink from /etc/systemd/system/dbus-org.fedoraproject.FirewallD1.service to /usr/lib/systemd/system/firewalld.service.
Created symlink from /etc/systemd/system/multi-user.target.wants/firewalld.service to /usr/lib/systemd/system/firewalld.service.
[root@nfsc ~]# systemctl status firewalld 
 firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2023-05-24 06:33:24 UTC; 4s ago
     Docs: man:firewalld(1)
 Main PID: 3034 (firewalld)
   CGroup: /system.slice/firewalld.service
           3034 /usr/bin/python2 -Es /usr/sbin/firewalld --nofork --nopid

May 24 06:33:23 nfsc systemd[1]: Starting firewalld - dynamic firewall daemon...
May 24 06:33:24 nfsc systemd[1]: Started firewalld - dynamic firewall daemon.
May 24 06:33:24 nfsc firewalld[3034]: WARNING: AllowZoneDrifting is enabled. This is considered an insecure configuration option. It will be removed in a future release. Please consider disabling it now.
~~~

 - Добавляем в/etc/fstab строку и выполняем команды:
~~~
[root@nfsc ~]# echo "192.168.56.10:/srv/share/ /mnt nfs vers=3,proto=udp,noauto,x-systemd.automount 0 0" >> /etc/fstab
[root@nfsc ~]# systemctl daemon-reload 
[root@nfsc ~]# systemctl restart remote-fs.target 
~~~

 - Заходим в директорию `/mnt/` и проверяем успешность монтирования:
~~~
[root@nfsc ~]# cd /mnt/
[root@nfsc mnt]# cd /mnt/systemctl restart remote-fs.targetdaemon-reload 
mount | grep mnt
systemd-1 on /mnt type autofs (rw,relatime,fd=46,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=25740)
192.168.56.10:/srv/share/ on /mnt type nfs (rw,relatime,vers=3,rsize=32768,wsize=32768,namlen=255,hard,proto=udp,timeo=11,retrans=3,sec=sys,mountaddr=192.168.56.10,mountvers=3,mountport=20048,mountproto=udp,local_lock=none,addr=192.168.56.10)
~~~


4. Проверка работоспособности

 - заходим на сервер:
~~~
alex@Ubuntu-Mak:~$ vagrant ssh nfss
~~~

 - заходим в каталог `/srv/share/upload`:
~~~
[vagrant@nfss ~]$ cd /srv/share/upload/
~~

 - создаём тестовый файл `touch check_file`:
~~~
[vagrant@nfss upload]$ sudo touch check_file
[vagrant@nfss upload]$ ls
check_file
~~~

 - заходим на клиент:
~~~
alex@Ubuntu-Mak:~$ vagrant ssh nfsc
~~~

 - заходим в каталог `/mnt/upload`:
~~~
[vagrant@nfsc upload]$ cd /mnt/upload/
~~~

 - проверяем наличие ранее созданного файла:
~~~
[vagrant@nfsc upload]$ ll
total 0
-rw-r--r--. 1 root root 0 May 24 07:00 check_file
~~~

 - создаём тестовый файл `touch_client_file`:
~~~
[vagrant@nfsc upload]$ sudo touch client_file
~~~

 - проверяем, что файл успешно создан:
~~~
[vagrant@nfsc upload]$ ls
check_file  client_file
~~~


5. Проверяем сервер

- заходим на сервер в отдельном окне терминала,
- перезагружаем сервер,
- заходим на сервер,
- проверяем наличие файлов в каталоге `/srv/share/upload/` - проверяем статус сервера NFS `systemctl status nfs` - проверяем статус firewall `systemctl status firewalld` - проверяем экспорты `exportfs -s`,
- проверяем работу RPC `showmount -a 192.168.56.10`
~~~
alex@Ubuntu-Mak:~$ vagrant ssh nfsc 
Last login: Wed May 24 06:59:33 2023 from 10.0.2.2

[vagrant@nfss ~]$ cd /srv/share/upload/
[vagrant@nfss upload]$ ls
check_file  client_file

[vagrant@nfss upload]$ systemctl status nfs
 nfs-server.service - NFS server and services
   Loaded: loaded (/usr/lib/systemd/system/nfs-server.service; enabled; vendor preset: disabled)
   Active: active (exited) since Wed 2023-05-24 06:20:18 UTC; 49min ago
  Process: 3221 ExecStartPost=/bin/sh -c if systemctl -q is-active gssproxy; then systemctl reload gssproxy ; fi (code=exited, status=0/SUCCESS)
  Process: 3204 ExecStart=/usr/sbin/rpc.nfsd $RPCNFSDARGS (code=exited, status=0/SUCCESS)
  Process: 3203 ExecStartPre=/usr/sbin/exportfs -r (code=exited, status=0/SUCCESS)
 Main PID: 3204 (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/nfs-server.service

[vagrant@nfss upload]$ systemctl status nfsfirewalld
 firewalld.service - firewalld - dynamic firewall daemon
   Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; vendor preset: enabled)
   Active: active (running) since Wed 2023-05-24 07:10:45 UTC; 1min 27s ago
     Docs: man:firewalld(1)
 Main PID: 404 (firewalld)
   CGroup: /system.slice/firewalld.service
           404 /usr/bin/python2 -Es /usr/sbin/firewalld --nofork --nopid

[vagrant@nfss upload]$ sudo exportfs -s 
/srv/share  192.168.56.11/32(sync,wdelay,hide,no_subtree_check,sec=sys,rw,secure,root_squash,no_all_squash)

[vagrant@nfss upload]$ sudo showmount -a 192.168.56.10
All mount points on 192.168.56.10:
192.168.56.11:/srv/share
~~~


6. Проверяем клиент: 

- возвращаемся на клиент 
- перезагружаем клиент 
- заходим на клиент 
- проверяем работу RPC `showmount -a 192.168.56.10` - заходим в каталог `/mnt/upload` 
- проверяем статус монтирования `mount | grep mnt` 
- проверяем наличие ранее созданных файлов 
- создаём тестовый файл `touch final_check` 
- проверяем, что файл успешно создан 
~~~
[vagrant@nfss upload]$ exit
logout
alex@Ubuntu-Mak:~$ vagrant ssh nfss c

Last login: Wed May 24 07:09:09 2023 from 10.0.2.2

[vagrant@nfsc ~]$ reboot
==== AUTHENTICATING FOR org.freedesktop.login1.reboot ===
Authentication is required for rebooting the system.
Authenticating as: root
Password: 
==== AUTHENTICATION COMPLETE ===
Connection to 127.0.0.1 closed by remote host.

alex@Ubuntu-Mak:~$ vagrant ssh nfsc 

Last login: Wed May 24 07:15:25 2023 from 10.0.2.2

[vagrant@nfsc ~]$ sudo -i

[root@nfsc ~]# showmount -a 192.168.56.10
All mount points on 192.168.56.10:

[root@nfsc ~]# cd /mnt/upload/

[root@nfsc upload]# ls

check_file  client_file

[root@nfsc upload]# mount | grep mnt
systemd-1 on /mnt type autofs (rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=10964)
192.168.56.10:/srv/share/ on /mnt type nfs (rw,relatime,vers=3,rsize=32768,wsize=32768,namlen=255,hard,proto=udp,timeo=11,retrans=3,sec=sys,mountaddr=192.168.56.10,mountvers=3,mountport=20048,mountproto=udp,local_lock=none,addr=192.168.56.10)

[root@nfsc upload]# touch final_check

[root@nfsc upload]# ls

check_file  client_file filan_check
~~~

