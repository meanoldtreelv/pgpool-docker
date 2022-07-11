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
FS01 - pgpool, pg-0
SD01 - pg-1
SD02 - pg2

Container Layout Abstract:

Pgpool exists on the same host as the fusion/freeswitch installation, it also conmtains the default master pg-# node
pg-# nodes exist on seperate docker instances to allow for some level of fault tolerance
all docker hosts are running on different metal


docker-compose deploymenr
there are two base files for deployment, fshost.yml and backup.yml. 
fshost.yml contains both the pgpool instance configuration as well as the initial pg-0 postgres server contianer





