
```
sudo ip route add 10.129.24.214/32 dev tun0
```

```
sudo ip route add 10.129.36.196/32 dev tun1
```

```
sudo ip route del 10.129.36.196/32 dev tun1
```

```
sudo ip route del 10.129.24.214/32 dev tun0
```


```
sudo ip route del 10.129.36.196/32 dev tun1  # Remove the old machine
sudo ip route add 10.129.50.50/32 dev tun1   # Add the new machine
```


```
sudo ip route replace 10.129.36.196/32 dev tun0
```

