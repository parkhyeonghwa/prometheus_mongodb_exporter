# Mongodb Exporter

Based on MongoDB exporter for prometheus.io, written in go (https://github.com/dcu/mongodb_exporter), but forked for full sharded support and structure changes.

### Experimental

The exporter is in beta/experimental state and field names are **very likely to change** and features may change or get removed!

### Features

- MongoDB Server Status metrics (*cursors, operations, indexes, storage, etc*)
- MongoDB Replica Set metrics (*members, ping, replication lag, etc*)
- MongoDB Replication Oplog metrics (*size, length in time, etc*)
- MongoDB Sharding metrics (*shards, chunks, db/collections, balancer operations*)
- MongoDB WiredTiger storage-engine metrics (*cache, blockmanger, tickets, etc*)

### Building

    export GO_VERSION=1.5.1  # if you wish to use your system version
    make

### Usage

The exporter can be started by running the '*mongodb_exporter*' binary that is created in the build step. The exporter will try to connect to '*mongodb://localhost:27017*' (no auth) as default if no options are supplied.

It is recommended to define the following options:

- **-mongodb.uri** - The URI of the MongoDB port (*default: mongodb://localhost:27017*)
- **-auth.user** - The optional auth username (*default: none*)
- **-auth.pass** - The optional auth password (*default: none*)
- **-web.listen-address** - The listen address of the exporter (*default: ":9001"*)
- **-log_dir** - The directory to write the log file (*default: /tmp*)

*For more options see the help page with '-h' or '--help'*

### Note about how this works
Point the process to any mongo port and it will detect if it is a mongos, replicaset member, or stand alone mongod and return the appropriate metrics for that type of node. This was done to preent the need to an exporter per type of process.

### Roadmap

- Document more configurations options here
- Stabilize WiredTiger support (*currently beta/experimental*)
- Add support for PerconaFT and RocksDB storage engines
- Write more go tests
- Version scheme

### Contact

- David Murphy - [Twitter](https://twitter.com/dmurphy_data) / [Github](https://github.com/dbmurphy) / [Email](mailto:david.murphy@percona.com)
- Tim Vaillancourt - [Github](https://github.com/timvaillancourt) / [Email](mailto:tim.vaillancourt@percona.com)
- Percona - [Twitter](https://twitter.com/Percona) / [Contact Page](https://www.percona.com/about-percona/contact)
