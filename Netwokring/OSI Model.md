
## **OSI Model Overview**
- **Purpose:** A conceptual framework (not a protocol suite) to describe how data moves across a network.
- **Use:** Provides a common language for IT professionals to discuss network functions and troubleshoot issues (e.g., "layer 3 problem").
- **Compatibility:** Works with various protocols (like TCP/IP, the most common suite today).

---

## **The 7 Layers (Top to Bottom)**
**Mnemonic:** **A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing

| Layer | Name         | Key Function & Examples                                                                                                                                 |
|-------|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| 7     | Application  | **User interaction** with applications (e.g., HTTP/HTTPS, FTP, DNS, email clients). Data you see on screen.                                            |
| 6     | Presentation | **Data translation/encryption** for the application layer (e.g., character encoding, SSL/TLS encryption/decryption).                                    |
| 5     | Session      | **Manages connections/sessions** between devices (e.g., establishes, maintains, and ends sessions; tunneling protocols).                                |
| 4     | Transport    | **End-to-end data transport** and reliability. Segments data; uses TCP (reliable, connection-oriented) or UDP (fast, connectionless). Port numbers used here. |
| 3     | Network      | **Logical addressing and routing** between networks. Uses IP addresses and subnet masks; routers operate here. Fragments packets if needed.              |
| 2     | Data Link    | **Node-to-node communication** on the same network. Uses MAC addresses (hardware addresses); switches operate here. Ethernet frames.                      |
| 1     | Physical     | **Physical signals and media**. Cables, fiber optics, wireless signals, voltages. Deals with bits.                                                     |

---

## **Key Points per Layer**

### **Layer 1: Physical**
- **Focus:** Physical medium (cables, fiber, wireless signals).
- **Troubleshooting:** Bad cables, interference, faulty hardware. Tests: loopback, cable checks.

### **Layer 2: Data Link**
- **Focus:** Communication between two directly connected devices.
- **Addressing:** MAC addresses (Media Access Control) or EUI-48/64.
- **Devices:** Network switches (forward frames based on MAC addresses).

### **Layer 3: Network**
- **Focus:** Routing between different networks.
- **Addressing:** IP addresses and subnet masks.
- **Devices:** Routers (forward packets based on IP addresses). Handles fragmentation.

### **Layer 4: Transport**
- **Focus:** Reliable data delivery between devices.
- **Protocols:** TCP (connection-oriented, reliable) and UDP (connectionless, fast).
- **Function:** Segments data, uses port numbers to direct traffic to applications.

### **Layer 5: Session**
- **Focus:** Manages dialogue between applications (start, stop, restart sessions).
- **Examples:** Control protocols, tunneling setups.

### **Layer 6: Presentation**
- **Focus:** Data formatting for the application (encryption, compression, encoding).
- **Common:** SSL/TLS for secure web traffic.

### **Layer 7: Application**
- **Focus:** Network services to end-user applications (what users interact with).
- **Examples:** Web browsers (HTTP/HTTPS), email clients, file transfers (FTP).

---

## **Practical Application: Wireshark Example**
A captured network frame in Wireshark can be mapped to OSI layers:

1. **Frame details (bytes on wire)** → **Layer 1** (Physical)
2. **Ethernet II (source/dest MAC)** → **Layer 2** (Data Link)
3. **Internet Protocol (IP addresses)** → **Layer 3** (Network)
4. **Transmission Control Protocol (TCP ports)** → **Layer 4** (Transport)
5. **SSL/TLS encryption** → **Layers 5-7** (Session, Presentation, Application combined in this case)

---

## **Why the OSI Model Matters**
- Provides a **standardized framework** for discussing network operations.
- Enables **targeted troubleshooting** (e.g., identifying if an issue is physical, addressing, or application-related).
- Facilitates communication among IT professionals universally.

