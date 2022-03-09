## Enumerate SNMP initial

```
snmpenum IP public linux.txt > snmp.txt
```

## Deeper

```
snmpwalk -c public -v2c -On IP > walk.txt
```