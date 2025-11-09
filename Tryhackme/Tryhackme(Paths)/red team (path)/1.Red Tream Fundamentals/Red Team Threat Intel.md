
<h3>Introduction</h3>

**Threat Intelligence (TI)** or **Cyber Threat Intelligence (CTI)** is the information, or TTPs (**T**actics, **T**echniques, and **P**rocedures), attributed to an adversary, commonly used by defenders to aid in detection measures. The red cell can leverage CTI from an offensive perspective to assist in adversary emulation.

<h3>Applying Threat Intel to the Red Team</h3>

Leveraging TTPs is used as a planning technique rather than something a team will focus on during engagement execution. Depending on the size of the team, a CTI team or threat intelligence operator may be employed to gather TTPs for the red team. During the execution of an engagement, the red team will use threat intelligence to craft tooling, modify traffic and behavior, and emulate the targeted adversary

These cyber frameworks will collect known TTPs and categorize them based on varying characteristics such as,

1. Threat Group
2. Kill Chain Phase
3. Tactic
4. Objective/Goal


<h3>The TIBER-EU Framework</h3>

**TIBER-EU** (**T**hreat **I**ntelligence-**b**ased **E**thical **R**ed Teaming) is a common framework developed by the European Central Bank that centers around the use of threat intelligence.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e73cca6ec4fcf1309f2df86/room-content/29c6b67582199ed69f1310348d29aa8c.svg)

The main difference between this framework and others is the _"Testing"_ phase that requires threat intelligence to feed the red team's testing


<h3>TTP Mapping</h3>

**TTP Mapping** is employed by the red cell to map adversaries' collected TTPs to a standard cyber kill chain. Mapping TTPs to a kill chain aids the red team in planning an engagement to emulate an adversary.

To begin the process of mapping TTPs, an adversary must be selected as the target. An adversary can be chosen based on,

1. Target Industry
2. Employed Attack Vectors
3. Country of Origin
4. Other Factors

The first cyber framework we will be collecting TTPs from is **[MITRE ATT&CK](https://attack.mitre.org/)

ATT&CK provides a basic summary of a group's collected TTPs. We can use **[ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/)** to help us visualize each TTP and categorize its place in the kill chain.

Going through the Navigator layer, we can assign various TTPs we want to employ during the engagement. Below is a compiled kill chain with mapped TTPs for **APT39**.

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5e73cca6ec4fcf1309f2df86/room-content/ce9424c66a674856de4c97613cbde8c4.png)

1. Reconnaissance:
    - No identified TTPs, use internal team methodology
2. Weaponization:
    - Command and Scripting Interpreter
        - PowerShell
        - Python
        - VBA
    - User executed malicious attachments
3. Delivery:
    - Exploit Public-Facing Applications
    - Spearphishing
4. Exploitation:
    - Registry modification
    - Scheduled tasks
    - Keylogging
    - Credential dumping
5. Installation:
    - Ingress tool transfer
    - Proxy usage
6. Command & Control:
    - Web protocols (HTTP/HTTPS)
    - DNS
7. Actions on Objectives
    - Exfiltration over C2

---

MITRE ATT&CK will do most of the work needed, but we can also supplement threat intelligence information with other platforms and frameworks. Another example of a TTP framework is **[OST Map](https://www.intezer.com/ost-map/)**.

OST Map provides a visual map to link multiple threat actors and their TTPs.


<h3>Creating a Threat Intel Driven Campaign</h3>

The task flow in this room logically follows the same path you would take as a red team to begin planning a campaign,  

1. Identify framework and general kill chain
2. Determine targeted adversary
3. Identify adversary's TTPs and IOCs
4. Map gathered threat intelligence to a kill chain or framework
5. Draft and maintain needed engagement documentation
6. Determine and use needed engagement resources (tools, C2 modification, domains, etc.)

**Lockheed Martin Cyber Kill Chain** and the **MITRE ATT&CK** framework.

|   |   |
|---|---|
|**Cyber Kill Chain**|**MITRE ATT&CK**|
|Recon|Reconnaissance|
|Weaponization|Execution|
|Delivery|Initial Access|
|Exploitation|Initial Access|
|Installation|Persistence / Defense Evasion|
|Command & Control|Command and Control|
|Actions on Objectives|Exfiltration / Impact|
