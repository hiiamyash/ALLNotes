

# Introduction

We focus on tools commonly available on standard systems to collect more information about the target. Being part of the system, such tools look innocuous and cause the least amount of "noise".

This room is organized as follows:

- Purpose of enumeration
- Linux enumeration with commonly-installed tools: System, users, networking, and running services
- MS Windows enumeration with built-in tools: System, users, networking, and running services
- Examples of additional tools: Seatbelt


# Purpose

Some of the information we are interested in gathering include:

- Users and groups
- Hostnames
- Routing tables
- Network shares
- Network services
- Applications and banners
- Firewall configurations
- Service settings and audit configurations
- SNMP and DNS details
- Hunting for credentials (saved on web browsers or client applications)


Furthermore, we might stumble upon sensitive data saved among the user’s documents or desktop directories. Think that someone might keep a `passwords.txt` or `passwords.xlsx` instead of a proper password manager. Source code might also contain keys and passwords left lurking around, especially if the source code is not intended to be made public.



# Linux Enumeration


Although some commands provide information on more than one area, we tried to group the commands into four categories depending on the information we expect to acquire.

- System
- Users
- Networking
- Running Services


##  System

we can get more information about the Linux distribution and release version by searching for files or links that end with `-release` in `/etc/`. Running `ls /etc/*-release`

```
ls /etc/*-release
/etc/centos-release  /etc/os-release  /etc/redhat-release  /etc/system-release

cat /etc/os-release 
NAME="CentOS Linux"
VERSION="7 (Core)"

```

We can find the system’s name using the command `hostname`.
```
user@TryHackMe$ hostname 
rpm-red-enum.thm
```

Various files on a system can provide plenty of useful information. In particular, consider the following `/etc/passwd`, `/etc/group`, and `/etc/shadow`. Any user can read the files `passwd` and `group`

```

$ cat /etc/group
root:x:0:
[...]
michael:x:1001:
peter:x:1002:
jane:x:1003:
randa:x:1004:

```

Similarly, various directories can reveal information about users and might contain sensitive files; one is the mail directories found at `/var/mail/`


```
ls -lh /var/mail/
```

To find the installed applications you can consider listing the files in `/usr/bin/` and `/sbin/`:

- `ls -lh /usr/bin/`
- `ls -lh /sbin/`

On an RPM-based Linux system, you can get a list of all installed packages using `rpm -qa`. The `-qa` indicates that we want to _query all_ packages.

On a Debian-based Linux system, you can get the list of installed packages using `dpkg -l`. The output below is obtained from an Ubuntu server.



## Users

Files such as `/etc/passwd` reveal the usernames; however, various commands can provide more information and insights about other users on the system and their whereabouts.

You can show who is logged in using `who`.
![[../../../../attchments/Pasted image 20250108225853.png]]

We can see that the user `root` is logged in to the system directly, while the users `jane` and `peter` are connected over the network, and we can see their IP addresses.

Note that `who` should not be confused with `whoami` which prints **your** effective user id


To take things to the next level, you can use `w`, which shows who is logged in and what they are doing. Based on the terminal output below, `peter` is editing `notes.txt` and `jane` is the one running `w` in this example.

![[../../../../attchments/Pasted image 20250108225946.png]]
To print the real and effective user and group IDS, you can issue the command `id` (for ID)




Do you want to know who has been using the system recently? `last` displays a listing of the last logged-in users; moreover, we can see who logged out and how much they stayed connected. In the output below, the user `randa` remained logged in for almost 17 hours, while the user `michael` logged out after four minutes.

![[../../../../attchments/Pasted image 20250108230216.png]]

Finally, it is worth mentioning that `sudo -l` lists the allowed command for the invoking user on the current system.


## Networking

The IP addresses can be shown using `ip address show` (which can be shortened to `ip a s`) or with the older command `ifconfig -a` (its package is no longer maintained.) The terminal output below shows the network interface `ens33` with the IP address `10.20.30.129` and subnet mask `255.255.255.0` as it is `24`.



The DNS servers can be found in the `/etc/resolv.conf`. Consider the following terminal output for a system that uses DHCP for its network configurations. The DNS, i.e. nameserver, is set to `10.20.30.2`.

![[../../../../attchments/Pasted image 20250109004828.png]]

`netstat` is a useful command for learning about network connections, routing tables, and interface statistics. We explain some of its many options in the table below.

|Option|Description|
|---|---|
|`-a`|show both listening and non-listening sockets|
|`-l`|show only listening sockets|
|`-n`|show numeric output instead of resolving the IP address and port number|
|`-t`|TCP|
|`-u`|UDP|
|`-x`|UNIX|
|`-p`|Show the PID and name of the program to which the socket belongs|

You can use any combination that suits your needs. For instance, `netstat -plt` will return _Programs Listening on TCP_ sockets. As we can see in the terminal output below, `sshd` is listening on the SSH port, while `master` is listening on the SMTP port on both IPv4 and IPv6 addresses. Note that to get all PID (process ID) and program names, you need to run `netstat` as root or use `sudo netstat`.

![[../../../../attchments/Pasted image 20250109004948.png]]

`netstat -atupn` will show _All TCP and UDP_ listening and established connections and the _program_ names with addresses and ports in _numeric_ format.

![[../../../../attchments/Pasted image 20250109005028.png]]

`lsof` stands for List Open Files. If we want to display only Internet and network connections, we can use `lsof -i`. The terminal output below shows IPv4 and IPv6 listening services and ongoing connections. The user `peter` is connected to the server `rpm-red-enum.thm` on the `ssh` port.

![[../../../../attchments/Pasted image 20250109005149.png]]
Because the list can get quite lengthy, you can further filter the output by specifying the ports you are interested in, such as SMTP port 25. By running `lsof -i :25`, we limit the output to those related to port 25,

![[../../../../attchments/Pasted image 20250109005235.png]]

## Running Services

or running services an processe

```
ps aux
```
![[../../../../attchments/Pasted image 20250109104247.png]]
`ps axjf`


# Windows Enumration

## System

One command that can give us detailed information about the system, such as its build number and installed patches, would be `systeminfo`. In the example below, we can see which hotfixes have been installed.

```
systeminfo
```

You can check installed updates using `wmic qfe get Caption,Description`. This information will give you an idea of how quickly systems are being patched and updated.

```
C:\>wmic qfe get Caption,Description
Caption                                     Description      
http://support.microsoft.com/?kbid=5013630  Update
https://support.microsoft.com/help/5013944  Security Update
                                            Update
```

You can check the installed and started Windows services using `net start`. Expect to get a long list; the output below has been snipped.

```
net start
```

If you are only interested in installed apps, you can issue `wmic product get name,version,vendor`. If you run this command on the attached virtual machine, you will get something similar to the following output.

```
C:\>wmic product get name,version,vendor
```

## Users

To know who you are, you can run `whoami`; moreover, to know what you are capable of, i.e., your privileges, you can use `whoami /priv`. An example is shown in the terminal output below.

Moreover, you can use `whoami /groups` to know which groups you belong to

```
whoami /priv
whoami /groups
```
You can view users by running `net user`.
```
net users
```

You can discover the available groups using `net group` if the system is a Windows Domain Controller or `net localgroup` otherwise

```
net group
net localgroup
```

You can list the users that belong to the local administrators’ group using the command `net localgroup administrators`.
```
net localgroup administrators
```

Use `net accounts` to see the local settings on a machine; moreover, you can use `net accounts /domain` if the machine belongs to a domain. This command helps learn about password policy, such as minimum password length, maximum password age, and lockout duration.


## Networking

You can use the `ipconfig` command to learn about your system network configuration. If you want to know all network-related settings, you can use `ipconfig /all`

`netstat -abno` showed that the server is listening on TCP ports 22, 135, 445 and 3389. The processes`sshd.exe`, `RpcSs`, and `TermService` are on ports `22`, `135`, and `3389`, respectively

```
ipconfig /all
netstat -abno
```


`arp -a` helps you discover other systems on the same LAN that recently communicated with your system. ARP stands for Address Resolution Protocol


# DNS, SMB, and SNMP


## DNS

`dig -t AXFR DOMAIN_NAME @DNS_SERVER`. The `-t AXFR` indicates that we are requesting a zone transfer, while `@` precedes the `DNS_SERVER` that we want to query regarding the records related to the specified `DOMAIN_NAME`.

```
dig -t AXFR DOMAIN_NAME @DNS_SERVER
```

## SMB

Server Message Block (SMB) is a communication protocol that provides shared access to files and printers. We can check shared folders using `net share`

```
ser@TryHackMe$ net share

Share name   Resource                        Remark

-------------------------------------------------------------------------------
C$           C:\                             Default share
IPC$                                         Remote IPC
ADMIN$       C:\Windows                      Remote Admin
Internal     C:\Internal Files               Internal Documents
Users        C:\Users
```

## SNMP

Simple Network Management Protocol (SNMP) was designed to help collect information about different devices on the network.

ne simple tool to query servers related to SNMP is `snmpcheck`. You can find it on the AttackBox at the `/opt/snmpcheck/` directory; the syntax is quite simple: `/opt/snmpcheck/snmpcheck.rb 10.10.34.124 -c COMMUNITY_STRING`.

```
/opt/snmpcheck/snmpcheck.rb 10.10.34.124 -c COMMUNITY_STRING
```



# More tools in CMD

This task mentions three options that are not built-in command-line tools:

- Sysinternals Suite
- Process Hacker
- GhostPack Seatbelt
### Sysinternals Suite

The [Sysinternals Suite](https://docs.microsoft.com/en-us/sysinternals/downloads/) is a group of command-line and GUI utilities and tools that provides information about various aspects related to the Windows system. To give you an idea, we listed a few examples in the table below.

|Utility Name|Description|
|---|---|
|Process Explorer|Shows the processes along with the open files and registry keys|
|Process Monitor|Monitor the file system, processes, and Registry|
|PsList|Provides information about processes|
|PsLoggedOn|Shows the logged-in users|

### Process Hacker

Another efficient and reliable MS Windows GUI tool that lets you gather information about running processes is [Process Hacker](https://processhacker.sourceforge.io/).


### GhostPack Seatbelt

[Seatbelt](https://github.com/GhostPack/Seatbelt), part of the GhostPack collection, is a tool written in C#. It is not officially released in binary form; therefore, you are expected to compile it yourself using MS Visual Studio.



# Summary Commands

| Linux Command     | Description                                    |
| ----------------- | ---------------------------------------------- |
| `hostname`        | shows the system’s hostname                    |
| `who`             | shows who is logged in                         |
| `whoami`          | shows the effective username                   |
| `w`               | shows who is logged in and what they are doing |
| `last`            | shows a listing of the last logged-in users    |
| `ip address show` | shows the network interfaces and addresses     |
| `arp`             | shows the ARP cache                            |
| `netstat`         | prints network connections                     |
| `ps`              | shows a snapshot of the current processes      |

| Windows Command  | Description                                                                              |
| ---------------- | ---------------------------------------------------------------------------------------- |
| `systeminfo`     | shows OS configuration information, including service pack levels                        |
| `whoami`         | shows the user name and group information along with the respective security identifiers |
| `netstat`        | shows protocol statistics and current TCP/IP network connections                         |
| `net user`       | shows the user accounts on the computer                                                  |
| `net localgroup` | shows the local groups on the computer                                                   |
| `arp`            | shows the IP-to-Physical address translation tables                                      |

