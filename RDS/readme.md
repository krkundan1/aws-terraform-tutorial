## Advantages of using RDS over EC2
* Automated provsioning and OS patching
* Continuous backup and restore to specific timestamp (PITR point in time recovery)
* Monitoring Dashboards
* Read Replicas for improved read performance
* Multi AZ setup for disaster recovery
* Scaling capability
* Storage backed by EBS (gp2, io2)

But you can't SSH to DB instance

## RDS - storage autoscaling
Helps to increase storage on RDS instance dynamically
when it sees the DB is running out of storage, it scales automatically
You have to set maximunm Threshold storage
Automatically modifies storage
 * if free storage is less than 5% of allocated storage
Useful for application with unpredictable workloads

## RDS read replicas for read scalability
Upto 15 read replicas with same AZ, different AZ or different region
Replication is ASYNC so eventually read is consistent
Replicas can be promoted to have own database and is out of replication and has its own lifecycle
Application must update the connection string to leverage read replicas

## RDS read replica network cost
* In AWS there is a network cost when data goes from one AZ to another
* In RDS if the read replicas are in different region then only network cost is there else replicas in same AZ no cost is there 

## RDS Multi AZ (Disaster Recovery)
* SYNC Replication
* One DNS name - automatic app failover to standby DB
* failover in case of AZ failure, netork failure, instance or storage failure
* not used for scaling

** Read replicas can be also set up for disaster recovery

## RDS from single AZ to Multi AZ
* Zero downtime operation (no need to stop DB instance)
* just click on modify for database
Following happens internally
  * A snapshot is taken
  * New DB is restored from snapshot in different AZ
  * Synchronization is established between two databases



