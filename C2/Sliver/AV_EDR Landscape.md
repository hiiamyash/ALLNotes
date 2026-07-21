
The AV/EDR Landscape

<h3>AV v EDR</h3>
Traditional AV
Signature-Based
Heuristic Analysis - charactristic and behaviour
Static Analysis

<h3>EDR</h3>
Advance / Proactive
Broader Range of Threats
Continuously monitor

**How it works**
Collects massive amounts of data
Analyze via ML & behavioral analytics
Automated Actions

<h3>Defender Overview</h3>
Key Features
Anomaly Detection
Cloud-Delivered
Protection
Behavioral Blocking


<h3>Static Evasion</h3>
**String Obfuscation**

- Base64/XOR  Encoding
- API Hashing

**Packing & Crypters**
- what is packing?
an self exracting Archive
this compersses ans wraps using small code called stub ,the malware
- whaat is Crypters 
this Enerytp the malware making it unbale to read

`LOLBAS`

<h3>Runtime Evasion</h3>
**Living Off the Land**

- Process Injection
- Thread Injection
- Process Hollowing
- Process Doppelganging
- Self-extracting archive
- Encryption
- Descrypt in memory

<h3>Process Injection</h3>

```
ps
```
`Get the PID of the process eeunned by your user`

```
migrate -p <PID>
```

### Stage & Stageless

<h3>Staged Payloads</h3>
Two Parts
**Stager**
Small piece of code
Connect back to C2
Download & execute

Sliverc2 custom satger written in NIM

**Stageless Payloads**
Significantly larger
Everything contained in payload
Potentially better for evasion, but harder to do

![](../../attchments/Pasted%20image%2020260720012615.png)

