# cloud-checklist

## database
* total how many clusters
* candidate master in place?
* slave replication behaviour on replication error
* orchestrator in place?
* ghost ready?
* pmm installed?
* slave lag metrics available
* slave lag metrics alerts in place
* snapshot creation in place
* is there any archival requirement?
* are snapshot policy in accordance with archival policy
* row or statement based replication
* mysql version being used?
* application using domain name or ip for connecting to db?
* separate slave and master for read and writes?
* slow query emails in place or not?
* cluster wise pt-kill setup or not? if yes then threshold values for slave and masters
* pt-kill query killed metrics and alert on that
* disk alert threshold in place or not?
* data type max limit breaching warning and alert in place or not?
* gtid enabled or not?
* deadlock scripts in place or not?

## elb checklist
* donot delete
* 4xx 5xx latency alerts
* unhealthy host alert


## ASG checklist
* desired=max alert
* desired=80% of max alert for big ASGS
* ASG config changed alert
* ASG instance health check enabled    (so that ASG does not consider unhealthy instance in ASG average cpu calculations used for auto scaling)
* ASG elb health check enabled          (ASG checks with elb if instance is healthy or not and doesnt consider that instance in cpu calculation)

## Elasticsearch checklist
* heap should be around 50% (tunable)
* instances should be termination protect
* If instances spawned via Auto scaling group then ASG scale in protect should be there to prevent accidental termination (been there faced that)
* monitoring metrics should be available
