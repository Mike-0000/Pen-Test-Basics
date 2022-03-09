## Directory Discovery

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
