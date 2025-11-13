┌──(sevenoffsec㉿antivenom)-[~/ctf/thm/linux/retro]
└─$ ffuf -u "http://retro.thm/FUZZ" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt 

retro                   [Status: 301, Size: 146, Words: 9, Lines: 2, Duration: 454ms]

![[../../../attchments/Pasted image 20250106232141.png]]

wp-content              [Status: 301, Size: 157, Words: 9, Lines: 2, Duration: 401ms]
wp-includes             [Status: 301, Size: 158, Words: 9, Lines: 2, Duration: 395ms]
wp-admin                [Status: 301, Size: 155, Words: 9, Lines: 2, Duration: 397ms]


