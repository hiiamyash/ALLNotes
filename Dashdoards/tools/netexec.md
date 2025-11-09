
```
nxc smb ip -u 'somehting' -p 'something' --shares
```

```
nxc smb administrator.htb -u "Olivia" -p "ichliebedich" --users
```

above command can give more information about the users and sometimes their passwords

```
nxc smb administrator.htb -u "Olivia" -p "ichliebedich" --rid-brute
```

above commad for user enum

```
e
```


```
nxc smb frizzdc.frizz.htb -k -u f.frizzle -p Jenni_Luvs_Magic23 --generate-krb5-file frizz.krb
```

Above will create an file called frizz.krb now if you copy that as krb5.conf to /etc then active directory can communicate better to your machine
```
sudo cp frizz.krb5 /etc/krb5.conf
```
