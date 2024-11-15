### Search exmaples.


```spl
index="prod_paloalto" sourcetype="pan:threat"
```

```spl
index="prod_paloalto" sourcetype="pan:traffic"  src_ip="85.208.136.157"
```

```spl
index="prod_paloalto" sourcetype="pan:traffic"  src_ip="213.174.201.17"
```

```spl
index="prod_paloalto" sourcetype="pan:traffic"  src_ip="85.208.136.157" | stats count, sum(bytes) 
```
```spl
- index="prod_paloalto" sourcetype="pan:log" dest_ip="85.208.136.157" | stats count, sum(bytes) as total_bytes by src_ip, dest_port
```

```spl
index="prod_paloalto" sourcetype="pan:threat"  dest_ip="85.208.136.157" | stats count, sum(bytes) as total_bytes by src_ip
```

```spl
index="prod_paloalto" sourcetype="pan:threat" dest_ip="85.208.136.157" |  head 100 - | tstats prestats=t count FROM datamodel=Network_Resolution where DNS.src IN ("65.193.168.6"), DNS.query IN ("*rackcdn.com*") by DNS.query DNS.src _time
| timechart count by DNS.src
```


#### Search user name and windows login
```spl 
index IN ("prod_windows", "prod_ejweb_windows") AYTGENERAL EventCode IN ("4625", "4624") 1.49.221.37
```


```spl 
index IN ("prod_windows", "prod_ejweb_windows") ej-enterprise-swissit-prod EventCode IN ("4625", "4624") 1.49.221.37
```

```spl
ej-enterprise-swissit-prod
| table signature dest Source_Workstation src_user src_ip user
```

