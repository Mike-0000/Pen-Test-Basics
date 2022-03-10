# Starting Penetration

```
msfconsole
```

To Open metasploit console

## Port Scan

```
nmap -sV -sC -O -p- -v --min-rate 20000 IP > nmap1.txt
```

##### Alternate

```
nmap -T4 -A -v IP  > nmap2.txt
```

##### UDP:

```
nmap -sU -sV IP -F -v > nmap3.txt
```

-O - OS Detection

-p- - to scan all ports

20k rate probably way too high. Reduce to reduce risk of alerting firewall.

-sS - for TCP SYN Scan

-sV - to show services related to each port

-sU - UDP Scan SLOW - only use if no where to go


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
