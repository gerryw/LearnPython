# Circonus

I had change the metrics report type from http servlet to statsD udp. If you want to check the result you can configure on circonus server or rollback the web.xml to use http servlet

Configure file: **cds.properties**

```
cds.circonus.host=10.255.2.21
cds.circonus.port=8125
#the unit is second
cds.circonus.period=60

```
**cds.circonus.host:** circonus server

**cds.circonus.port** circonus port

**cds.circonus.period** data send period, the unit is second

**Notice:**

* Don't use the same method name for same resource's same http method