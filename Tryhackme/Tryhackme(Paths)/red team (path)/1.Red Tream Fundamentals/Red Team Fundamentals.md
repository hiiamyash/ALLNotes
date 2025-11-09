
<h3>Vulnerability Assessment and Penetration Tests Limitations</h3>

To summarize, a vulnerability assessment focuses on scanning hosts for vulnerabilities as individual entities so that security deficiencies can be **identified** and effective security measures can be deployed to **protect** the network in a prioritized manner. Most of the work can be done with automated tools and performed by operators without requiring much technical knowledge.

<h3>Advanced Persistent Threats and why Regular Pentesting is not Enough</h3>

- **Penetration tests are LOUD:** Usually, pentesters won't put much effort into trying to go undetected. Unlike real attackers, they don't mind being easy to detect, as they have been contracted to find as many vulnerabilities as they can in as many hosts as possible.
- **Non-technical attack vectors might be overlooked:** Attacks based on social engineering or physical intrusions are usually not included in what is tested.
- **Relaxation of security mechanisms:** While doing a regular penetration test, some security mechanisms might be temporarily disabled or relaxed for the pentesting team in favor of efficiency.

red team engagements consist of emulating a real threat actor's **Tactics, Techniques and Procedures (TTPs)** so that we can measure how well our blue team responds to them and ultimately improve any security controls in place.



<h3>Engagement Structure</h3>

In this room, we will commonly reference the "Lockheed Martin Cyber Kill Chain."

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5ed5961c6276df568891c3ea/room-content/33e4c2dc2ab851b11654ae61953a7df1.png)

Components of the kill chain are broken down in the table below.

| Technique             | Purpose                                                                           | Examples                                         |
| --------------------- | --------------------------------------------------------------------------------- | ------------------------------------------------ |
| Reconnaissance        | Obtain information on the target                                                  | Harvesting emails, OSINT                         |
| Weaponization         | Combine the objective with an exploit. Commonly results in a deliverable payload. | Exploit with backdoor, malicious office document |
| Delivery              | How will the weaponized function be delivered to the target                       | Email, web, USB                                  |
| Exploitation          | Exploit the target's system to execute code                                       | MS17-010, Zero-Logon, etc.                       |
| Installation          | Install malware or other tooling                                                  | Mimikatz, Rubeus, etc.                           |
| Command & Control     | Control the compromised asset from a remote central controller                    | Empire, Cobalt Strike, etc.                      |
| Actions on Objectives | Any end objectives: ransomware, data exfiltration, etc.                           | Conti, LockBit2.0, etc.                          |



