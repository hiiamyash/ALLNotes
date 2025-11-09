
```
ip tuntap add user root mode tun ligolo
ip link set ligolo up
```

```
./proxy -selfcert
```

```
./agent.exe -connect 192.168.1.5:11601 -ignore-cert
```


```
ip route add 192.168.98.0/24 dev ligolo
ip route list
```

```
sudo ip route replace 192.168.98.0/24 dev ligolo
```

```
sudo ip route del 172.16.1.0/24 dev ligolo
```

```
sudo ip route add 172.16.0.0/23 dev ligolo scope link
```

```
session
start
```


./agent -connect 10.10.14.166:11601 -ignore-cert