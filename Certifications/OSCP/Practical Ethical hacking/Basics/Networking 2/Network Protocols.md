#networking #basics
## Smba (139,445)

![[../../../../../attchments/Pasted image 20250104222820.png]]

## rpcbind (111)

`rpcbind` is a system service that facilitates communication between Remote Procedure Call (RPC) programs on a network. It listens for requests on a specific port and maps them to the correct port where the desired RPC service is running. This is necessary because RPC services often use dynamic port assignments, making it difficult to directly contact a service without `rpcbind`.

**`rpcbind` Simplified**  
`rpcbind` acts like a receptionist in a company, directing incoming calls (requests) to the right department (service) that has a changing office number (port).

**Corporate Example:**  
In a file-sharing setup like NFS, when a computer needs a file, it asks `rpcbind` where to find the NFS service. `rpcbind` tells it the right port, enabling the file transfer. Without `rpcbind`, the computer wouldn’t know where to connect.





#### **IMAP**

- **Usage**: Allows users to access and manage their email directly on the server, maintaining synchronization across devices.
- **Features**:
    - Email remains on the server until explicitly deleted.
    - Supports folder management and marking messages as read/unread.
    - Ideal for accessing email from multiple devices.
- **Ports**: Typically operates on port 143 (unencrypted) and port 993 (encrypted with SSL/TLS).

#### **POP3**

- **Usage**: Downloads emails to the local device and deletes them from the server by default (configurable to retain emails).
- **Features**:
    - Emails are primarily stored locally after download.
    - Simpler protocol compared to IMAP.
- **Ports**: Typically uses port 110 (unencrypted) and port 995 (encrypted with SSL/TLS).





