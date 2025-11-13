
The tasks of this room cover the following topics:

- Types of reconnaissance activities
- WHOIS and DNS-based reconnaissance
- Advanced searching
- Searching by image
- Google Hacking
- Specialized search engines
- Recon-ng
- Maltego

Some specific objectives we'll cover include:

- Discovering subdomains related to our target company
- Gathering publicly available information about a host and IP addresses
- Finding email addresses related to the target
- Discovering login credentials and leaked passwords
- Locating leaked documents and spreadsheets

Active recon can be classified as:

1. **External Recon**: Conducted outside the target's network and focuses on the externally facing assets assessable from the Internet. One example is running Nikto from outside the company network.
2. **Internal Recon**: Conducted from within the target company's network. In other words, the pentester or red teamer might be physically located inside the company building. In this scenario, they might be using an exploited host on the target's network. An example would be using Nessus to scan the internal network using one of the target’s computers.


<h1>Built-in tools</h1>

`whois` provides us with:

- Registrar WHOIS server
- Registrar URL
- Record creation date
- Record update date
- Registrant contact info and address (unless withheld for privacy)
- Admin contact info and address (unless withheld for privacy)
- Tech contact info and address (unless withheld for privacy)

![Pasted image 20241207235843](../../../../attchments/Pasted%20image%2020241207235843.png)

DNS queries can be executed with many different tools found on our systems, especially Unix-like systems. One common tool found on Unix-like systems, Windows, and macOS is `nslookup`

![Pasted image 20241208000019](../../../../attchments/Pasted%20image%2020241208000019.png)

another tool commonly found on Unix-like systems is `dig`, short for Domain Information Groper (dig). `dig` provides a lot of query options and even allows you to specify a different DNS server to use. For example, we can use Cloudflare's DNS server: `dig @1.1.1.1 tryhackme.com`

![Pasted image 20241208000148](../../../../attchments/Pasted%20image%2020241208000148.png)

![Pasted image 20241208000257](../../../../attchments/Pasted%20image%2020241208000257.png)


The final tool that ships with Unix-like systems is `traceroute`, or on MS Windows systems, `tracert`. As the name indicates, it traces the route taken by the packets from our system to the target host. The console output below shows that `traceroute` provided us with the routers (hops) connecting us to the target system. It's worth stressing that some routers don’t respond to the packets sent by `traceroute`, and as a result, we don’t see their IP addresses; a `*` is used to indicate such a case.

![Pasted image 20241208000443](../../../../attchments/Pasted%20image%2020241208000443.png)

In summary, we can always rely on:

- `whois` to query the WHOIS database
- `nslookup`, `dig`, or `host` to query DNS servers

WHOIS databases and DNS servers hold publicly available information, and querying either does not generate any suspicious traffic.

Moreover, we can rely on Traceroute (`traceroute` on Linux and macOS systems and `tracert` on MS Windows systems) to discover the hops between our system and the target host.


<h1>Advanced Searching</h1>

| Symbol / Syntax                  | Function                                            |
| -------------------------------- | --------------------------------------------------- |
| `"search phrase"`                | Find results with exact search phrase               |
| `OSINT filetype:pdf`             | Find files of type `PDF` related to a certain term. |
| `salary site:blog.tryhackme.com` | Limit search results to a specific site.            |
| `pentest -site:example.com`      | Exclude a specific site from results                |
| `walkthrough intitle:TryHackMe`  | Find pages with a specific term in the page title.  |
| `challenge inurl:tryhackme`      | Find pages with a specific term in the page URL.    |
In addition to `pdf`, other filetypes to consider are: `doc`, `docx`, `ppt`, `pptx`, `xls` and `xlsx`.

Examples of confidential information include:

- Documents for internal company use
- Confidential spreadsheets with usernames, email addresses, and even passwords
- Files containing usernames
- Sensitive directories
- Service version number (some of which might be vulnerable and unpatched)
- Error messages

GHDB contains queries under the following categories:

- **Footholds**  
    Consider [GHDB-ID: 6364](https://www.exploit-db.com/ghdb/6364) as it uses the query `intitle:"index of" "nginx.log"` to discover Nginx logs and might reveal server misconfigurations that can be exploited.
- **Files Containing Usernames**  
    For example, [GHDB-ID: 7047](https://www.exploit-db.com/ghdb/7047) uses the search term `intitle:"index of" "contacts.txt"` to discover files that leak juicy information.
- **Sensitive Directories**  
    For example, consider [GHDB-ID: 6768](https://www.exploit-db.com/ghdb/6768), which uses the search term `inurl:/certs/server.key` to find out if a private RSA key is exposed.
- **Web Server Detection**  
    Consider [GHDB-ID: 6876](https://www.exploit-db.com/ghdb/6876), which detects GlassFish Server information using the query `intitle:"GlassFish Server - Server Running"`.
- **Vulnerable Files**  
    For example, we can try to locate PHP files using the query `intitle:"index of" "*.php"`, as provided by [GHDB-ID: 7786](https://www.exploit-db.com/ghdb/7786).
- **Vulnerable Servers**  
    For instance, to discover SolarWinds Orion web consoles, [GHDB-ID: 6728](https://www.exploit-db.com/ghdb/6728) uses the query `intext:"user name" intext:"orion core" -solarwinds.com`.
- **Error Messages**  
    Plenty of useful information can be extracted from error messages. One example is [GHDB-ID: 5963](https://www.exploit-db.com/ghdb/5963), which uses the query `intitle:"index of" errors.log` to find log files related to errors.



Now we'll explore two additional sources that can provide valuable information without interacting with our target:

- Social Media
- Job ads

<h3>Social Media</h3>

it's worthwhile checking the following:

- LinkedIn
- Twitter
- Facebook
- Instagram

<h3>Job ads</h3>

	Job advertisements can also tell you a lot about a company. In addition to revealing names and email addresses, job posts for technical positions could give insight into the target company’s systems and infrastructure. The popular job posts might vary from one country to another.


Note that the [Wayback Machine](https://archive.org/web/) can be helpful to retrieve previous versions of a job opening page on your client’s site.

![Pasted image 20241208003024](../../../../attchments/Pasted%20image%2020241208003024.png)

<h1>Specialized Search Engines</h1>

### WHOIS and DNS Related

Beyond the standard WHOIS and DNS query tools that we covered in Task 3, there are third parties that offer paid services for historical WHOIS data. One example is WHOIS history

we'll focus on key DNS related aspects. We will consider the following:

- [ViewDNS.info](https://viewdns.info/)
- [Threat Intelligence Platform](https://threatintelligenceplatform.com/)

### ViewDNS.info

[ViewDNS.info](https://viewdns.info/) offers _Reverse IP Lookup_. Initially, each web server would use one or more IP addresses; however, today, it is common to come across shared hosting servers. With shared hosting, one IP address is shared among many different web servers with different domain names. With reverse IP lookup, starting from a domain name or an IP address, you can find the other domain names using a specific IP address(es).

In the figure below, we used reverse IP lookup to find other servers sharing the same IP addresses used by `cafe.thmredteam.com`
![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/a6a57e946b742bf9439430c1669382a5.png)

### Threat Intelligence Platform

[Threat Intelligence Platform](https://threatintelligenceplatform.com/) requires you to provide a domain name or an IP address, and it will launch a series of tests from malware checks to WHOIS and DNS queries. The WHOIS and DNS results are similar to the results we would get using `whois` and `dig`, but Threat Intelligence Platform presents them in a more readable and visually appealing way. There is extra information that we get with our report. For instance, after we look up `thmredteam.com`, we see that Name Server (NS) records were resolved to their respective IPv4 and IPv6 addresses, as shown in the figure below.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/8ba0fec5aad89cfb7c3d242ed92c9da4.png)

### Specialized Search Engines

#### Censys

[Censys Search](https://search.censys.io) can provide a lot of information about IP addresses and domains. In this example, we look up one of the IP addresses that `cafe.thmredteam.com` resolves to. We can easily infer that the IP address we looked up belongs to Cloudflare

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/efc8f98cc9e721707d4bad477340e120.png)

#### Shodan

Let’s demonstrate a simple example of looking up information about one of the IP addresses we got from `nslookup cafe.thmredteam.com`. Using `shodan host IP_ADDRESS`, we can get the geographical location of the IP address and the open ports, as shown below.

![Pasted image 20241208004535](../../../../attchments/Pasted%20image%2020241208004535.png)

![Pasted image 20241208004706](../../../../attchments/Pasted%20image%2020241208004706.png)


<h1>Recon-ng</h1>


Here is a concise summary of the process along with all the necessary commands to use Recon-ng effectively:
Steps and Commands
1. Start Recon-ng with a Specific Workspace

To start Recon-ng and specify a workspace, use:
```
recon-ng -w clinicredteam
```


2. Create a New Workspace

If the workspace does not exist, create it with:

```
workspaces create clinicredteam
```

3. Add Initial Information to the Database

Insert initial data (e.g., a domain name) into the database:

```
db insert domains
domain (TEXT): clinicredteam.com
notes (TEXT):
```

4. Explore the Marketplace

Search for modules that might be useful:

```
marketplace search <keyword>
```

For example, to find modules related to domains:

```
marketplace search domains-
```

5. Get Information About a Specific Module

Before installing a module, learn what it does:

```
marketplace info <module_name>
```

Example:

```
marketplace info recon/domains-hosts/google_site_web
```

6. Install a Module

Install a module from the marketplace:

```
marketplace install <module_name>
```

Example:

```
marketplace install recon/domains-hosts/google_site_web
```

#### 7.Load and Run a Module

To work with an installed module, first load it:

```
modules load <module_name>
```

Example:

```
modules load recon/domains-hosts/google_site_web
```

List available options for the loaded module:

```
options list
```

Set necessary options (if required):

```
options set <option_name> <value>
```

Run the loaded module:

```
run
```

8. Manage API Keys (If Required)

Some modules require API keys. Add a key using:

```
keys add <key_name> <key_value>
```

List keys to check what is set:

```
keys list
```

Remove a key if necessary:

```
keys remove <key_name>
```

9. Exit Recon-ng

To exit the tool, type:

```
exit
```

Explanation

    Workspaces allow you to manage investigations separately.
    Database commands help seed and query initial target data.
    Marketplace commands enable searching, installing, and understanding modules.
    Modules commands let you load, configure, and execute specific reconnaissance tasks.
    Key management ensures compatibility with modules requiring API integrations.