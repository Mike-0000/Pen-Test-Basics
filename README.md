# Pen-Test-Basics
 
```msfconsole```

To Open metasploit console

## Starting Penetration

### Port Scan

```nmap IP  -sV --min-rate 20000```

20k rate probably way too high. Reduce to reduce risk of alerting firewall.

-sS for TCP SYN Scan

-sV to show services related to each port


#### Get Version of Service

NetCat

```nc IP PORT```


### Web Server:

#### Directory Discovery

Word lists are at `/usr/share/wordlists` (In KALI)

```gobuster dir -u URL:port -t threads -w <word list location>```


## Attempt to Elevate permissions after entry

##### Run Inside of Meterpreter

```run post/multi/recon/local_exploit_suggester```

Gives readout of possible vulnerabilities of connected host

### NFS (RPCBIND?)

Enumerate NFS shares.

```nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount 10.10.223.98```



### Samba share

```nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse IP```

Change port to match nmap results. (Usually 139 or 445)


##### Inspect Samba Share

```smbclient //ip/sambashare```


You can recursively download the SMB share too.

```smbget -R smb://ip/sambashare```