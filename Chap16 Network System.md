# Chap 16 Network System

### Several Common Commandline

* **ping** : Send an ICMP ECHO REQUEST to network hosts

* **traceroute** : Print the route packets trace to a network host

* **netstat** : Print network connections, routing tables, interface statistics, masquerade connections,and multicast memberships

* **ifconfig** : Used to configure a network interface in Linux

* **ftp** : Internet file transfer program

* **wget** : Non-interactive network downloader

* **ssh** : OpenSSH SSH client (remote login program)

* **nslookup** : Resolve the Hostname of Domain Name

* **scp/sftp** : Make use of an SSH encryptedtunnel to copy files across the network


### Examples of Commandlines

* **ping** : 

```
jiazhen@ubuntu:~$ ping linuxcommand.org
PING linuxcommand.org (216.34.181.97) 56(84) bytes of data.
64 bytes from vhost.sourceforge.net (216.34.181.97): icmp_seq=1 ttl=128 time=62.3 ms
64 bytes from vhost.sourceforge.net (216.34.181.97): icmp_seq=2 ttl=128 time=63.9 ms
```

```
jiazhen@ubuntu:~$ ping 216.58.194.174
PING 216.58.194.174 (216.58.194.174) 56(84) bytes of data.
64 bytes from 216.58.194.174: icmp_seq=1 ttl=128 time=16.4 ms
64 bytes from 216.58.194.174: icmp_seq=2 ttl=128 time=15.6 ms
64 bytes from 216.58.194.174: icmp_seq=3 ttl=128 time=30.5 ms
```


* **netstat** : used to examine various network settings and statistics.

  **PS:** The first, called eth0, is the Ethernet interface and the second, called lo, is the loopback interface, a virtual interface that the system uses to “talk to itself.” "**UP**" means the network interface is enabled. 

```
jiazhen@ubuntu:~$ netstat -ie
Kernel Interface table
ens33     Link encap:Ethernet  HWaddr 00:0c:29:70:8a:1b  
          inet addr:192.168.116.144  Bcast:192.168.116.255  Mask:255.255.255.0
          inet6 addr: fe80::7e4:2d14:741:4d48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4890500 (4.8 MB)  TX bytes:88477 (88.4 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:24101 (24.1 KB)  TX bytes:24101 (24.1 KB)
```

* **netstat -r** : “-r”option will display the kernel’s network routing table. This shows howthe network is configured to send packets from network to network

```
jiazhen@ubuntu:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
default         192.168.116.2   0.0.0.0         UG        0 0          0 ens33
link-local      *               255.255.0.0     U         0 0          0 ens33
192.168.116.0   *               255.255.255.0   U         0 0          0 ens33
```

* **ifconfig** :

```
jiazhen@ubuntu:~$ ifconfig
ens33     Link encap:Ethernet  HWaddr 00:0c:29:70:8a:1b  
          inet addr:192.168.116.144  Bcast:192.168.116.255  Mask:255.255.255.0
          inet6 addr: fe80::7e4:2d14:741:4d48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4917199 (4.9 MB)  TX bytes:92241 (92.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:25051 (25.0 KB)  TX bytes:25051 (25.0 KB)
```

* **nslookup** :

```
jiazhen@ubuntu:~$ nslookup google.com
Server:		127.0.1.1
Address:	127.0.1.1#53

Non-authoritative answer:
Name:	google.com
Address: 172.217.5.110
```

* **wget** : Can be used for file downloading

```
jiazhen@ubuntu:~$ wget http://linuxcommand.org/index.php
--2017-11-04 22:56:11--  http://linuxcommand.org/index.php
Resolving linuxcommand.org (linuxcommand.org)... 216.34.181.97, 216.34.181.97
Connecting to linuxcommand.org (linuxcommand.org)|216.34.181.97|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4153 (4.1K) [text/html]
Saving to: ‘index.php’

index.php           100%[===================>]   4.06K  --.-KB/s    in 0s      

2017-11-04 22:56:11 (463 MB/s) - ‘index.php’ saved [4153/4153]

```


* **ssh** : Method to solve issue with remote host ID changed error. 

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@ WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED! @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
06:ea:f1:f8:db:75:5c:0c:af:15:d7:99:2d:ef:08:2a.
Please contact your system administrator.
Add correct host key in /home/user/.ssh/known_hosts to get rid of this message.
Offending key in /home/user/.ssh/known_hosts:4
RSA host key for domain.com has changed and you have requested strict checking.
Host key verification failed.
```

**Solution1:** 

```
ssh-keygen -R [your domain name or IP address]
```

**Solution2:** 

Delete Offending key in /home/user/.ssh/known_hosts:4 from /.ssh/known__hosts


* **scp** :

```
[me@linuxbox ~]$ scp bob@remote-sys:document.txt
```


* **sftp** : 

```
[me@linuxbox ~]$ sftp remote-sysConnecting to remote-sys...me@remote-sys's password:sftp> lsubuntu-8.04-desktop-i386.isosftp> lcd Desktopsftp> get ubuntu-8.04-desktop-i386.isoFetching /home/me/ubuntu-8.04-desktop-i386.iso to ubuntu-8.04-desktop-i386.iso/home/me/ubuntu-8.04-desktop-i386.iso 100% 699MB 7.4MB/s 01:35sftp> bye
```
