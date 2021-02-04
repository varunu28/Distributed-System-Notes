# Distributed Storage

## Hadoop
 - Used MapReduce API
 - MapReduce job management
 - Uses Distributed filesystem (HDFS)
 - Works as an ecosystem with multiple underlying technology such as `HBase`, `Hive`, `Pig` etc
 
## HDFS (Hadoop distributed file system)
 - Consists of files and directories
 - Metadata managed by replicated `master`
 - Files stored in large, immutable, replicated blocks
 - Consists of `Name Node` & `Data Nodes`
 - Clients talk to `Name Node` to get the address of data on the `Data Nodes`
 - Follows the principle of `Moving the compute where the data is` rather than pulling the data for doing computation
 
