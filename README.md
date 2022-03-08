# Pen-Test-Basics
 
```msfconsole```
To Open metasploit console

## Starting Penetration

####Web Server:

#####Directory Discovery

Word lists are at `/usr/share/wordlists`

```gobuster dir -u URL:port -w <word list location>```


## Attempt to Elevate permissions after entry

#####Run Inside of Meterpreter
```run post/multi/recon/local_exploit_suggester```
Gives readout of possible vulnerabilities of connected host