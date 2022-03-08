# Pen-Test-Basics
 
```msfconsole```
To Open metasploit console

## Starting Penetration

###Port Scan

```nmap IP  -sV --min-rate 20000```

20k rate probably way too high. Reduce to reduce risk of alerting firewall.

-sS for TCP SYN Scan
-sV to show services related to each port


####Web Server:

#####Directory Discovery

Word lists are at `/usr/share/wordlists`

```gobuster dir -u URL:port -t threads -w <word list location>```


## Attempt to Elevate permissions after entry

#####Run Inside of Meterpreter

```run post/multi/recon/local_exploit_suggester```
Gives readout of possible vulnerabilities of connected host