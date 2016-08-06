# telegraf
## use exec plugin
-for windows:  commands=["*.bat"], format = influx 
-for linux:    commands=["/etc/bin/ab.py" ],format=json 
### win *.bat
-echo cpu,host=xi'an vaule=1
###  ab.py
>-!/usr/bin/env python
-import commands
-import json
-
-output = {}
-raw = commands.getstatusoutput('vmstat -s')
-raw = raw[1].split('\n')
-
-for row in raw:
-    value = int(row.split()[0])
-    key = ' '.join(row.split()[1:])
-    output[key] = value
-
-print json.dumps(output)
