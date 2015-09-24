= Life after Postgres
* Reminder: Chatham House Rules
* Who is using postgres?
* What have you outgrown is a question to ask?
* Discussion around a specific use case with time series data, partitioned per user
  * The access pattern tends to be a key question, so just the latest data can be a specific use case
  * Subdividing into date based tables requires manual partitioning, but that can be done
  * But access patterns make a huge difference
  * Lots of options, offline clustering after a day, various other options
  * Can start playing with file systems to use filesystems for seek
  * So look at Log, Structure, Merge (i.e. Bigtable, Cassandra, HBase etc)
  * stuff is always laid out on disk
  * much faster to write and scale cassandra, but scarier to read if things go wrong (less familiar)
  * number of nodes on Cassandra: 6 - Why? Seemed about the right number based on amount of storage and replica numbers
  * Trade off, lacking expertise for easier sharding
* Anybody migrated off of postgres?
  * Reasonable sized elastic search data cluster,
  * It will occasionally blow up in JVM GC hell, but not as much anymore
  * Default agreegation queries, will load everything into memory, using dot-values means it may stream, which prevents some GC stuff.
  * Replays data into elasticsearch if htere is a serious problem, which isn't too bad, only needed in case of an upgrade
  * Query around postgres's handling of text search tools, as compared with elasticsearch
* how about automatic failover, say in cloud situations
  * It appears to be possible, pgbouncer and stuff, floating ip's
* Postgres has some neat features around foreign table support, allowing querying on external data sources and post insert trigger denormalisation.
* Is htere a confidence that you can get about Postgres's ability to write bits to disk compared to the convienence of developers ability to use the database.
* People are getting increasingly abstracted away from the physical hardware, so being aware of the writes going to disk
* Amazon RDS, which offers Postgres, MySql as well as Aurora
* Anyone using Hive based tooling?
  * Looked at HBase, but it looked like too many moving parts
  * Some queries are not sensible for asking, had tried Redshift, but concurrency issues cause some problems
