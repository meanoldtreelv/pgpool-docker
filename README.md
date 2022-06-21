# pgpool-docker

split node/swarm implementation of bitnami's pgpool-docker cluster design. 

Compute Node Layout

SD01 - 10.3.34.205
SD01 - 10.3.34.206
FS01 - 10.4.60.11

Container List

pg-# - Postgres data shard with repmgr replication engine
pgpool - pgpool ha broker


Container Layout
FS01 - pgpool
SD01 - pg-0
SD02 - pg-1

Container Layout Abstract:

Pgpool exists on the same host as the fusion/freeswitch installation
pg-# nodes exist on seperate docker instances to allow for some level of fault tolerance
all docker hosts are running on different metal





