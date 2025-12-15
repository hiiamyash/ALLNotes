


---

### : Networking Functions

_The protocols and rules that manage traffic flow._

#### **Content Delivery Network (CDN)**

- **Concept:** A network of servers placed all over the world to store (cache) copies of your website's content closer to the user22.
    
- **Technical Example:** If you are in New York watching a Netflix video, you stream it from a CDN server in New York, not from the main headquarters in California. This reduces lag (latency)23.
    

#### **VPN (Virtual Private Network)**

- **Concept:** A secure, encrypted tunnel through the public internet. It lets you work from a coffee shop (insecure) as if you were sitting inside your secure office building24.
    
- **VPN Concentrator:** A dedicated hardware appliance built to handle the heavy encryption work for thousands of employees connecting at once25252525.
    

#### **Quality of Service (QoS)**

- **Concept:** Traffic prioritization. You tell the network which data is "VIP" and which can wait26.
    
- **Technical Example:** You configure your router to give **Voice over IP (VoIP)** phone calls "High Priority" and file downloads "Low Priority." This ensures your phone call doesn't sound robotic even if someone is downloading a huge file at the same time27272727.
    

#### **Time to Live (TTL)**

_A "Self-Destruct" timer for data._

- **1. TTL in Routing (Loop Prevention)**
    
    - **The Problem:** If routers get confused, a packet could loop in a circle forever (A -> B -> A -> B)28.
        
    - **The Fix:** The packet has a "Hop Limit" (TTL). Every time it passes a router, the number goes down by 1. When it hits 0, the packet is killed (dropped)29.
        
    - **Value:** Linux defaults to 64 hops; Windows defaults to 12830.
        
- **2. TTL in DNS (Caching Timer)**
    
    - **The Problem:** When you look up a website's IP, you don't want to ask the DNS server every single second.
        
    - **The Fix:** The DNS record has a TTL in **seconds** (e.g., 300 seconds). Your computer remembers the IP for 5 minutes. After the timer expires, it deletes the memory and asks the server again31313131.