--------- Rust scann

┌──(sevenoffsec㉿antivenom)-[~/ctf/thm/windows/yearoftheowl]
└─$ rustscan -a 10.10.193.121             
.----. .-. .-. .----..---.  .----. .---.   .--.  .-. .-.
| {}  }| { } |{ {__ {_   _}{ {__  /  ___} / {} \ |  `| |
| .-. \| {_} |.-._} } | |  .-._} }\     }/  /\  \| |\  |
`-' `-'`-----'`----'  `-'  `----'  `---' `-'  `-'`-' `-'
The Modern Day Port Scanner.
________________________________________
 --------------------------------------
Breaking and entering... into the world of open ports.

[~] The config file is expected to be at "/home/sevenoffsec/snap/rustscan/208/.rustscan.toml"
[!] File limit is lower than default batch size. Consider upping with --ulimit. May cause harm to sensitive servers
[!] Your file limit is very small, which negatively impacts RustScan's speed. Use the Docker image, or up the Ulimit with '--ulimit 5000'. 
Open 10.10.193.121:80
Open 10.10.193.121:445
Open 10.10.193.121:3389
Open 10.10.193.121:47001
[~] Starting Script(s)
Couldn't open a raw socket. Error: Permission denied (13)
[!] Error Exit code = 1


Found an new port
47001


