# Splunk spl query examples

### Find the number of failed logins per use datamodel "Authentication"

```spl
from datamodel:"Authentication" 
search is_Failed_Authentication = 1
stats count by user
```

### Give the number of logs in the main index by severity in the past hour. _by hostname_


#### Use the stats command.

```spl
index=main sourcetype=syslog
  host=<hostname>
  earliest=1h@h
  stats count by severity
```


### How to use the eval command.  
#### _(Eval is use to cream a new searchable field)_

#### This example creates a new field based on the values in existing fields field1, and field2

```spl
eval new_field = field1 + field2
```


### Show webserver errors

### 

```spl
index=weblogs sourcetype=access_combined 
status>=400 | table _time, method, uri, status
```

### Search in a specific index 

#### Show data for destination IP address from the specific index. Show thes the last 100 entries.

```spl 
index="prod_paloalto" 
  sourcetype="pan:threat" 
  dest_ip="85.208.136.157" 
  earliest=1@h |  
  head 100
```


### Splunk indexes list

#### Splunk Log Index Name
1. prod_windows
1. prod_aws
1. prod_paloalto
1. prod_ciscoasa
1. prod_ejweb_windows
1. prod_linux
1. prod_umbrella
1. prod_0365
1. prod_15
1. prod_akamal
1. prod_paloalto_pci
1. prod_ejweb_cloudtrail
1. prod_qualys
1. prod_broadcom
1. prod_15_pci
1. prod_linux_pci
1. prod_voltage_pci
1. prod_netscaler
1. prod_ping
1. prod_carbonblack
1. prod_netography
1. prod_intune
1. prod_airwatch
1. prod_trendmicro
1. prod_cyberark
1. prod_pulsesecure_pci
1. prod_microsoftgraph
1. prod_tacacsplus
1. prod_f5
1. prod_f5_cde


---
