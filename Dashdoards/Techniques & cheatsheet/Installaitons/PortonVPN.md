
```


sudo rm -f /usr/share/keyrings/protonvpn.gpg

sudo apt install curl -y
curl -fsSL https://repo.protonvpn.com/debian/public_key.asc | sudo gpg --dearmor -o /usr/share/keyrings/protonvpn.gpg

echo "deb [signed-by=/usr/share/keyrings/protonvpn.gpg] https://repo.protonvpn.com/debian stable main" | sudo tee /etc/apt/sources.list.d/protonvpn.list


sudo apt update

sudo apt install protonvpn

```