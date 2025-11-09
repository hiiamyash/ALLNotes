## How DNS Works

Globallydistributed DNS servers translate domain names into IP addresses and thus control which
server a user can reach via a particular domain. There are several types of DNS servers that
are used worldwide:

- DNS root server
- Authoritative name server
- Non-authoritative name server
- Caching server
- Forwarding server
- Resolver

Of course. Here is the expanded table with an added column containing concise, professional definitions suitable for an interview setting.

### DNS Servers Explained for a Technical Interview

| Server Type                      | Simple Explanation (What it does)                                                                                           | Easy Analogy / Example                                                                                                                       | Technical Definition (For an Interview)                                                                                                                                                                                                                                                          |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **DNS Root Server**              | The main index of the internet. It knows where to send requests based on the domain's ending (like `.com` or `.in`).        | You ask, "Where can I find `google.com`?" The Root Server says, "Go talk to the `.com` TLD server."                                          | The Root Server sits at the apex of the DNS hierarchy. Its primary function is to respond to iterative queries for the Top-Level Domain (TLD) by providing a referral to the TLD's authoritative nameservers.                                                                                    |
| **Authoritative Nameserver**     | The ultimate source of truth for a specific domain. It holds the official address record.                                   | The Authoritative Server for `google.com` holds the official record and tells you, "The IP address for `google.com` is **142.250.193.110**." | An Authoritative Nameserver holds and serves the DNS resource records (e.g., A, AAAA, MX, CNAME) for a specific zone. It provides definitive answers to queries about domains under its control and is the ultimate source of truth for that zone's data.                                        |
| **Non-authoritative Nameserver** | A server that gives an answer it learned from another server. The information isn't official but is from a reliable source. | Asking a fellow library visitor who just looked up the book's location. Their answer is correct, but they aren't the official librarian.     | A server that provides a DNS record from its cache rather than from the original source zone file. The response from a non-authoritative server will not have the Authoritative Answer (AA) bit set in its header.                                                                               |
| **Caching DNS Server**           | A server that remembers recent answers to speed things up for everyone.                                                     | Your local librarian keeps a sticky note with the locations of popular books to answer requests instantly.                                   | A server that caches responses to DNS queries for a duration specified by the record's Time-To-Live (TTL). Its purpose is to reduce latency for subsequent queries to the same domain and decrease the load on authoritative nameservers.                                                        |
| **Forwarding Server**            | A server that just passes questions along to another, pre-configured DNS server.                                            | A trainee librarian who doesn't look up answers but instead asks a senior librarian and relays the response back to you.                     | A DNS server configured to pass queries it cannot resolve from its cache to an upstream DNS server, known as a forwarder. This centralizes DNS traffic and can simplify management and security policy enforcement.                                                                              |
| **Resolver**                     | The component on your device or network that starts the whole DNS lookup process for you.                                   | This is **you** or your personal assistant starting the search by going to the front desk and making the initial request.                    | Also known as a Recursive Resolver, this server accepts a hostname query from a client and takes full responsibility for resolving it. It performs a series of iterative queries to the root, TLD, and authoritative servers until it finds the IP address, which it then returns to the client. |


Imagine you want to visit a website like `www.example.com`. You type this friendly domain name into your browser, but your computer doesn't understand words – it speaks the language of numbers, specifically IP addresses. So, how does your computer find the website's IP address? Enter DNS, the internet's trusty translator.

![Flowchart showing two main sections: User Database and Data Collection. Includes steps like 'Check User', 'Send to Source Database', 'Store Data', and 'Send to UI System'.](https://mermaid.ink/svg/pako:eNptkk1uwjAQha8y8rpcIItWkAAtUNQmlSrksDDxlEQQT-QfJIS4ex2nNG1arzx-n5-ex3NhBUlkEdtr0ZSwSnMFfhm36w425DTEVDfOou60do15XGJxMBCLosQtjEb3MLk8vcCMnJIP156ceA3WFIiYZ6ikgWSdwatDfQZLkKKh4wn1dnBngyZceuQxKYWFNS39jjtTWfyCvdsgb2t9c-wN4-CU_A7dy8mPjFOeYuG0qU4IK6KDa4bgLdjck9ZpZcC_20e7dWmYbRroGU-JLKxFjZCh7h88C_KCv62Sf9RFUJd87GxJurLCtsH-cssuUlfMu8blit2xGnUtKul_-NKKObMl1pizyG-l0Iec5erqOeEsZWdVsMhqh3dMk9uXLPoQR-Mr10hhMamE73L9fYqysqSfuwEKc3T9BOe0sj4)

1. `Your Computer Asks for Directions (DNS Query)`: When you enter the domain name, your computer first checks its memory (cache) to see if it remembers the IP address from a previous visit. If not, it reaches out to a DNS resolver, usually provided by your internet service provider (ISP).
    
2. `The DNS Resolver Checks its Map (Recursive Lookup)`: The resolver also has a cache, and if it doesn't find the IP address there, it starts a journey through the DNS hierarchy. It begins by asking a root name server, which is like the librarian of the internet.
    
3. `Root Name Server Points the Way`: The root server doesn't know the exact address but knows who does – the Top-Level Domain (TLD) name server responsible for the domain's ending (e.g., .com, .org). It points the resolver in the right direction.
    
4. `TLD Name Server Narrows It Down`: The TLD name server is like a regional map. It knows which authoritative name server is responsible for the specific domain you're looking for (e.g., `example.com`) and sends the resolver there.
    
5. `Authoritative Name Server Delivers the Address`: The authoritative name server is the final stop. It's like the street address of the website you want. It holds the correct IP address and sends it back to the resolver.
    
6. `The DNS Resolver Returns the Information`: The resolver receives the IP address and gives it to your computer. It also remembers it for a while (caches it), in case you want to revisit the website soon.
    
7. `Your Computer Connects`: Now that your computer knows the IP address, it can connect directly to the web server hosting the website, and you can start browsing.