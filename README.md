# pgpool-docker

split node/swarm implementation of bitnami's pgpool-docker cluster design. 

Compute Node Layout

SD01 - 10.3.34.205
SD01 - 10.3.34.206
FS01 - 10.4.60.11
FSREPORTS - 10.3.34.209

Container List

pg-# - Postgres data shard with repmgr replication engine
pgpool - pgpool ha broker


Container Layout
SD01 - pg-1, pgpool (for now)
SD02 - pg2

Container Layout Abstract:

Pgpool exists on the same host as the fusion/freeswitch installation, it also conmtains the default master pg-# node
pg-# nodes exist on seperate docker instances to allow for some level of fault tolerance
all docker hosts are running on different metal

Swarm overlay netowork allows any Manager node (including Drain nodes) to access servies as if they were running on 127.0.0.1

Sentriumdev Info

Reporting DB server:
fsreports.docker
10.3.34.209
shell user:fsreports
shell pass:fsreports
database connection info
RW DB on :5432
RO DB on :15432
user: postgres
pass: adminpassword