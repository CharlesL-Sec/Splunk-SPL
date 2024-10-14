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

#### Output by table arranged by time 

```spl
index=weblogs sourcetype=access_combined 
status>=400 | table _time, method, uri, status
```


---
