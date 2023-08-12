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
* Disable apparmour as it can restart database due to mem usage restriction.
* Teams replicating from database given new cluster info (hive , datalake etc)

## elb checklist
* donot delete
* 4xx 5xx latency alerts
* unhealthy host alert


## ASG checklist
* ASG auto scaling policy is decided and configured in aws
* desired=max alert
* desired=80% of max alert for big ASGS
* ASG config changed alert
* ASG instance health check enabled    (so that ASG does not consider unhealthy instance in ASG average cpu calculations used for auto scaling)
* ASG elb health check enabled          (ASG checks with elb if instance is healthy or not and doesnt consider that instance in cpu calculation)
* Multiple instance types are allowed in ASG auto scaling
* ASG instance type prioritisation checkout out in aws.

## Elasticsearch checklist
* heap should be around 50% (tunable)
* instances should be termination protect
* If instances spawned via Auto scaling group then ASG scale in protect should be there to prevent accidental termination (been there faced that)
* monitoring metrics should be available
* Data partition is pointed to disk with sufficient intended storage or not? because we have seen that by mistake data partition can point to low size root disk which causes production issues

## jenkins cron job
* cron expression to run periodically if required
* description of what cron does
* retry cron setting to retry in case of failure
* slack or email integration to notify of failures
* cron timeouts in jenkins jobs so that jobs doesnt stay stuck forever not leading to any alert

## kafka checklist
* Data partition is pointed to disk with sufficient intended storage or not? because we have seen that by mistake data
* When adding a new kafka instance along with zookeeper hosted on it. always check that zookeeper has become part of cluster or not

## zookeeper checklist
* when adding a new zookeeper instance, you will have to add its ip in all of the zookeeper instances , and take restart of complete cluster to make it recognized in the cluster.
*   partition can point to low size root disk which causes production issues
