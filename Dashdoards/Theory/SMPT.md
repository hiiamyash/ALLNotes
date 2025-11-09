**What is SMTP?**

SMTP (Simple Mail Transfer Protocol) is the internet's standard protocol for **sending emails**. Its job is to push emails from a sender's mail server to a recipient's mail server. It is usually paired with protocols like IMAP or POP3, which are used for _receiving_ and accessing emails from a server.

**Key Information:**

- **Ports:** SMTP uses several key ports:
    
    - **Port 25:** The standard port for server-to-server email transfer.
        
    - **Port 587:** The modern, preferred port for email clients to submit outgoing mail to a server. It requires authentication and uses encryption (`STARTTLS`).
        
    - **Port 465:** An older port used for secure email submission with SSL/TLS encryption from the start.
        
- **Security:** By default, SMTP is unencrypted and sends data in plain text. To protect privacy and prevent spam, modern SMTP uses:
    
    - **SSL/TLS Encryption:** To secure the connection.
        
    - **SMTP-Auth:** An authentication mechanism that forces users to log in with a username and password before they can send email, preventing unauthorized use.
        
- **How it Works (The Agents):**
    
    1. Your email client (**MUA**) sends your email to your outgoing mail server.
        
    2. The server's **MTA** (Mail Transfer Agent) looks up the recipient's mail server using DNS.
        
    3. Your MTA connects to the recipient's MTA and transfers the email.
        
    4. Finally, the recipient's server uses an **MDA** (Mail Delivery Agent) to place the email into the correct mailbox.
        
- **Major Vulnerability:** A misconfigured server that doesn't require authentication can become an **Open Relay**, allowing anyone to use it to send spam.