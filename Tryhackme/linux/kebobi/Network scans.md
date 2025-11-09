### rustscan

Open 10.10.20.36:21
Open 10.10.20.36:22
Open 10.10.20.36:111
Open 10.10.20.36:80
Open 10.10.20.36:139
Open 10.10.20.36:445
Open 10.10.20.36:2049
Open 10.10.20.36:36199
Open 10.10.20.36:39007
Open 10.10.20.36:58479
Open 10.10.20.36:59921

### namp scan


21/tcp    open  ftp         ProFTPD 1.3.5
22/tcp    open  ssh         OpenSSH 7.2p2 Ubuntu 4ubuntu2.7 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 b3:ad:83:41:49:e9:5d:16:8d:3b:0f:05:7b:e2:c0:ae (RSA)
|   256 f8:27:7d:64:29:97:e6:f8:65:54:65:22:f7:c8:1d:8a (ECDSA)
|_  256 5a:06:ed:eb:b6:56:7e:4c:01:dd:ea:bc:ba:fa:33:79 (ED25519)
80/tcp    open  http        Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Site doesn't have a title (text/html).
| http-robots.txt: 1 disallowed entry 
|_/admin.html
111/tcp   open  rpcbind     2-4 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100003  2,3,4       2049/tcp   nfs
|   100003  2,3,4       2049/tcp6  nfs
|   100003  2,3,4       2049/udp   nfs
|   100003  2,3,4       2049/udp6  nfs
|   100005  1,2,3      39007/tcp   mountd
|   100005  1,2,3      39802/udp   mountd
|   100005  1,2,3      50371/udp6  mountd
|   100005  1,2,3      53035/tcp6  mountd
|   100021  1,3,4      36199/tcp   nlockmgr
|   100021  1,3,4      36559/udp   nlockmgr
|   100021  1,3,4      38013/tcp6  nlockmgr
|   100021  1,3,4      40801/udp6  nlockmgr
|   100227  2,3         2049/tcp   nfs_acl
|   100227  2,3         2049/tcp6  nfs_acl
|   100227  2,3         2049/udp   nfs_acl
|_  100227  2,3         2049/udp6  nfs_acl
139/tcp   open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp   open  netbios-ssn Samba smbd 4.3.11-Ubuntu (workgroup: WORKGROUP)
2049/tcp  open  nfs         2-4 (RPC #100003)
36199/tcp open  nlockmgr    1-4 (RPC #100021)
39007/tcp open  mountd      1-3 (RPC #100005)
58479/tcp open  mountd      1-3 (RPC #100005)
59921/tcp open  mountd      1-3 (RPC #100005)



┌──(sevenoffsec㉿antivenom)-[~/ctf/thm/linux/kenobi]
└─$ nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount 10.10.255.39
Starting Nmap 7.94SVN ( https://nmap.org ) at 2025-01-05 14:43 IST
Nmap scan report for 10.10.255.39
Host is up (0.41s latency).

PORT    STATE SERVICE
111/tcp open  rpcbind
| nfs-statfs: 
|   Filesystem  1K-blocks  Used       Available  Use%  Maxfilesize  Maxlink
|_  /var        9204224.0  1836508.0  6877120.0  22%   16.0T        32000
| nfs-ls: Volume /var
|   access: Read Lookup NoModify NoExtend NoDelete NoExecute
| PERMISSION  UID  GID  SIZE  TIME                 FILENAME
| rwxr-xr-x   0    0    4096  2019-09-04T08:53:24  .
| rwxr-xr-x   0    0    4096  2019-09-04T12:27:33  ..
| rwxr-xr-x   0    0    4096  2019-09-04T12:09:49  backups
| rwxr-xr-x   0    0    4096  2019-09-04T10:37:44  cache
| rwxrwxrwx   0    0    4096  2019-09-04T08:43:56  crash
| rwxrwsr-x   0    50   4096  2016-04-12T20:14:23  local
| rwxrwxrwx   0    0    9     2019-09-04T08:41:33  lock
| rwxrwxr-x   0    108  4096  2019-09-04T10:37:44  log
| rwxr-xr-x   0    0    4096  2019-01-29T23:27:41  snap
| rwxr-xr-x   0    0    4096  2019-09-04T08:53:24  www
|_
| nfs-showmount: 
|_  /var *

Nmap done: 1 IP address (1 host up) scanned in 12.57 seconds


-------------Priority list

- [x] port 80
- [x] port 139
- [ ] port 445
- [ ] port 2049
- [ ] port 21