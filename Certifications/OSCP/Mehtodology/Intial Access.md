

Web Enumration

## Command

- [ ] nmap
- [ ] rustscan
- [ ] Version for all Services

## Port 80

- [ ] wapalizer
- [ ] robots.txt
- [ ] security.txt
- [ ] directory Fuzzing
- [ ] Scourse code of very page
- [ ] Version of Product
- [ ] V-host
- [ ] Nikto
- [ ] Making notes of every input feild

# Service Enumeration

## Active Directory Specific

```

PORT     STATE SERVICE
53/tcp   open  domain
88/tcp   open  kerberos-sec
135/tcp  open  msrpc
139/tcp  open  netbios-ssn
389/tcp  open  ldap
445/tcp  open  microsoft-ds
464/tcp  open  kpasswd5
593/tcp  open  http-rpc-epmap
636/tcp  open  ldapssl
3268/tcp open  globalcatLDAP
3269/tcp open  globalcatLDAPssl
```

## Identify the Local Domain

Next, we should check the `nmap` output for the [RootDSE](https://www.ibm.com/docs/en/zos/2.4.0?topic=considerations-root-dse&ref=benheater.com) and any potential hostname (e.g. `DC01.domain.tld`)

add this to you /etc/hosts

```
target_ip='10.10.10.22'

sudo nmap -Pn --script ldap-rootdse.nse $target_ip

If you've only run a basic `nmap` scan and need to enumerate the RootDSE
```

```
target_ip='10.10.10.22'
target_domain='domain.tld'
target_hostname="DC01.${target_domain}"

echo -e "${target_ip}\t\t${target_domain} ${target_hostname}" | sudo tee -a /etc/hosts`
```



## DNS

If we've established the local domain for the Active Directory environment, we should attempt to enumerate any DNS records for use when assessing other protocols.


Attempt a zone transfer from the DNS server on the target. If configured correctly, the zone transfer should be refused.

```
target_ip='10.10.10.22'
target_domain='domain.tld'
host -T -l $target_domain $target_ip
```

If the zone transfer fails, you can try and manually enumerate records in the target domain

```
target_ip='10.10.10.22'

target_domain='domain.tld'

dns_wordlist='/usr/share/seclists/Discovery/DNS/namelist.txt'

gobuster dns -r $target_ip -d $target_domain -w $dns_wordlist -t 100
```



## LDAP

A quick win would be the ability to enumerate LDAP records anonymously, as this would allow us to gather a great deal of information about interesting users, groups, and other domain records.


```
target_domain='domain.tld'
target_hostname="DC01.${target_domain}"
domain_component=$(echo $target_domain | tr '\.', '\n' | xargs -I % echo "DC=%" | paste -sd, -)

ldapsearch -x -H ldap://$target_hostname -b $domain_component
```

after entering the above command you shhould see an error

saying that a successful bind must be completed, meaning you need a credential


if not

```
ldapsearch -x -H ldap://$target_hostname -b $domain_component 'objectClass=*'
```


using the above command you are able to anonymously query LDAP, this is an example command to pull everything from LDAP



if you want to do more than go to this website https://notes.benheater.com/books/active-directory/page/ldapsearch?ref=benheater.com


## SMB

If we can connect to SMB anonymously, it's worth checking to see if we can enumerate object RIDs anonymously as well. RID cycling would allow us to enumerate a list of users and groups on the computer for further use during testing.

```
target_ip='10.10.10.22'
smbclient -N -L //$target_ip
```

If you can connect to SMB with a null session (and maybe even list shares), we can try and enumerate more and potentially map shares

```
smbclient -N //$target_ip/share_name

Connect to a SMB share via null session
```

```
# nxc replaces crackmapexec
nxc smb $target_ip -u 'anonymous' -p '' --rid-brute 3000
nxc smb $target_ip -u '' -p '' --rid-brute 3000




If configured correctly, you should see a permissions error, indicating the tests have failed

```





## Kerberos

if you have not found usernames we are find username using a wordlist


If we've found some usernames, we can then see if any of them are configured with `UF_DONT_REQUIRE_PREAUTH`, pull some AS-REP hashes, and attempt to crack them offline.


Deduplicate and Save a List of Usernames to Spray at the KDC

```

cat /usr/share/wordlists/seclists/Usernames/xato-net-10-million-usernames.txt | tr '[:upper:]' '[:lower:]' | sort -u > kerberos_users.txt


```


**Use Kerbrute to Enumerate Valid Usernames**

```
kerbrute userenum -d domain.tld --dc dc-ip-here -t 100 -o kerbrute.log ./kerberos_users.txt
```


**Attempting to find AS-REP hashes**

```

cat kerbrute.log
grep '@' kerbrute.log | awk -v FS=' ' '{print $7}' | cut -d '@' -f 1 > as_rep_test.txt
cat as_rep_test.txt


```




```
domain_controller=dc1.domain.tld
domain='domain.tld'
username_list='/usr/share/seclists/Usernames/top-usernames-shortlist.txt'
nmap -Pn -p88 --script krb5-enum-users --script-args krb5-enum-users.realm=$domain,userdb=$username_list $domain_controller
```




## General Procedure

This is my generalized approach to every target:

1. File servers
2. Web servers
3. Everything else


#### 1. ***File servers** — FTP/SMB

- May allow anonymous access or may be configured with default credentials
- This is an _****excellent opportunity****_ to gather more information from files
- Additional information may include usernames, passwords, config files, etc
- This information maybe useful when assessing other services



#### 2. Web — HTTP/HTTPS

- Web is just as simple as opening your web browser
- Navigate to the target IP or domain name and just start clicking around
- Make a note of potential input points that could be abused
- Web pages may contain usernames, passwords, interesting source code, etc


#### 3. Everything else

- Start probing other ports, try to understand how they behave
- Lots of Googling, probably something on HackTricks about it
- Try other `nmap` scans to see if additional ports are revealed; UDP or X-Mas scans, for example.


## DNS — UDP/53 & TCP/53

I'm putting this one at the top — above file servers — because this is one of those easy things you can try that can be potentially high-impact.

If you found — for example — in your `nmap` scan that a web server had a TLS certificate with a `commonName=mysite.test` and there is a DNS server running, [you should test to see if a zone transfer is possible](https://learn.microsoft.com/en-us/troubleshoot/windows-server/networking/dns-works-on-tcp-and-udp?ref=benheater.com).

```
target_domain='mysite.test'
target_ip='10.10.100.44'
host -T -l $target_domain $target_ip
```

Using the `host` command `-l` requests a zone transfer



```
target_ip='10.10.100.44'
target_domain='mysite.test'
dns_wordlist='/usr/share/seclists/Discovery/DNS/namelist.txt'

gobuster dns -r $target_ip -d $target_domain -w $dns_wordlist -t 100
```

If the zone transfer fails, you can try and manually enumerate records in the target domain


## FTP — TCP/21

```

ftp anonymous@10.10.100.44
```


When prompted for a password, simply press the `Enter` key

- `ls` to list files on the server
- `get` to retrieve files on the server
- `less` or `more` to read files from the FTP shell
- `cd` to change into any potential directories
- `put` to test write permissions as a way to perhaps chain an exploit with another service

We're trying to uncover:

- Usernames
- Passwords
- Configuration files
- Source code
- Backups
- Anything interesting

## SMB — TCP/139 & TCP/445

#### List Shares

```
smbclient -N -L //10.10.100.44
```


No username specified, and '-N' for passwordless authentication

#### Mapping Shares


```
smbclient -N //10.10.100.44/myshare
```

If you are able to map the share anonymously, try the following:

- `ls` to list files on the server
- `get` to retrieve files on the server
- `less` or `more` to read files from the SMB shell
- `cd` to change into any potential directories
- `put` to test write permissions as a way to perhaps chain an exploit with another service


## HTTP — TCP/80 & TCP/443


#### Initial Questions

The first things I want to establish with the web service are:

- Are there any noticeable differences between the `http://` and the `https://` versions of the apps running on the web server? In other words, is `http://` redirecting to `https://`, are they duplicates, or are they completely different in behavior and presentation?
- Is the server making use of any `ServerName` (virtual host) directives that would cause different pages to load depending on the the hostname the client requests?

#### Test the Raw IP Address

- `http://10.10.100.44`
- `https://10.10.100.44`

- If the server loads different content at each unique scheme
    - There are distinct configurations per port
    - Plan on testing the servers independently

#### Testing Virtual Hosts

look for vhost then add that to the /etc/hosts


#### Walking the Happy Path


do every things an normal user will do click links understand fuctions authentication as an user


#### Checking the Page Source



look for anything interesting visible client side

- Typically in the HTML comments
- Usernames
- Passwords
- Directory names
- File names
- Etc


#### Check for Robots and Sitemap


#### Directory and File Enumeration

```
gobuster dir -u http://10.10.100.44 -w /usr/share/seclists/Discovery/Web-Content/directory-list-big.txt -x php,html -t 100 -o gobuster80.txt

gobuster dir -k -u https://dev.mysite.test -w /usr/share/seclists/Discovery/Web-Content/big.txt -x php,html -t 100 -o gobuster443.txt
```

```
`wp-scan` can be helpful when enumerating WordPress
```


#### Testing the Application

You want to begin testing the web applications at various points:

- Vulnerable service or plugin versions
- URL parameters
- Login forms
- Search fields
- File uploads
- Etc.

And, you could test for things like:

- Path traversal
- Local and/or remote file inclusion
- Content type filter bypass
- SQL injection
- Default credentials
- Credential stuffing
- Password spraying
- Much, much more

## Unknown Ports and Services


use netcat for banner grabbing


if you find an new port or service search somehting like

You could search something like: `tcp 1883 mqtt pentest`


## Information Re-Use

If you've discovered useful information while probing HTTP or some other service, you should always consider how this information may be able to be used with services you previously looked at.






