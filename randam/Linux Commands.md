
# ls

## Description

Lists the contents of a director
## Usage

- `ls [options] [file/directory]`

![Pasted image 20250614095310](../attchments/Pasted%20image%2020250614095310.png)


# pwd


## Description

Prints the full path of the current working directory.

## USage

`pwd`

![Pasted image 20250614095730](../attchments/Pasted%20image%2020250614095730.png)

# cat

## Description

Displays the content of files, concatenates files, or creates files.

## USage

`cat [location of the file]`

![Pasted image 20250614095922](../attchments/Pasted%20image%2020250614095922.png)


# rm -rf

## Description

This command help in removing the file or directory it does it recursivly and forcefully

## Usage

`rm -rf [name of the file or Directory]`

![Pasted image 20250614100556](../attchments/Pasted%20image%2020250614100556.png)

# echo

## Description

Used to Print an string or store that string in an file

## Usage

`echo 'your string' >> file`


![Pasted image 20250614100833](../attchments/Pasted%20image%2020250614100833.png)


# mkdir

## Description

Helps in making directories

## Usage

`mkdir [name of the directory]`

![Pasted image 20250614101125](../attchments/Pasted%20image%2020250614101125.png)
# openvpn

## Description

Used to Connect to an vpn using it's ovpn file

## Usage

`sudo openvpn [name of your vpn file]`

![Pasted image 20250614101334](../attchments/Pasted%20image%2020250614101334.png)

# ifconfig

## Description

Used to Display information regarding network interfaces

## Usage 

`ifconfig`

![Pasted image 20250614101738](../attchments/Pasted%20image%2020250614101738.png)


# ps

## Description

used to display the running process in your enviroment

## Usage

`ps -aux`


# find 

## Description

Used to Find any file or directory

## Usage

`find / -type f -perm -4000 2>/dev/null`


![Pasted image 20250614095209](../attchments/Pasted%20image%2020250614095209.png)


# managing users and groups


```
useradd name
sudo useradd -m john
passwd john
userdel john
useradd -m newuser123
useradd -r name
usermod -l john test123



groupadd sales
cat /etc/group

groupmod -m purcahse saler

chage -l nandita
chage -m 5 nandita
chage -M 10 nandita

echo "nandita:hello123" | chpasswd

gpasswd -a nandita developer
above is used for adding user to the group

su newuser


```



```
ls 
ls -l --> listing files with perm
ls -a --> hidden files
ls -h  --> humar readable

```


```
pkill -u kali

usermod -l base kali
usermod -d /home/base -m base
chown -R base:base /home/base

groupadd base
usermod -g base base
chown -R base:base /home/base

sudo reboot
```


```
-d -> chesks if the directory exits or not

-r -> readable or not
-w -> writeable or not
-x -> executeable or not
-s -> checks if the directory has data or not
-f -> Human Redable format
```

```
* -> for all files or Directories
# -> for using Commanenst display
/ -> dor using comments
@ -> selecting a partiular authentication
"" -> Displaying The data in which the user had written 
```






```
Assignment

what is meant by scrippting 
what is the use of #! lines?

what are the types of scripting techniques

how can you execute the bash script


hwo can you execute thhe bash sci



write the steps to ptint 1 to 10 numbers using case

write basic kali linux kali linux commands with examples

what is the differnce between files and directories

what are the debugging techniques


```


# AIM
```
expirement with diffrent tricks of executing shell script

find different ways of executing an bash script

practise textprocessing by writing a script to seach for a specif pattern in a file using grep
```

```
bash filename.sh

./filename.sh

sh filename.sh


```


