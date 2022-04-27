# hello-world

## Introduction

This is a simple spark app.

## Environment

- sbt 1.6.2
- Scala 2.13.8
- Spark 3.2.1
- Ubuntu 20.04

## Bug reproduction

Both of the following two cases trigger errors like `NoSuchFileException`, which are expected to run successfully.

### `sbt run` in one shot

```bash
sbt run
```

Errors go as

```bash
[info] welcome to sbt 1.6.2 (Oracle Corporation Java 11)
[info] loading settings for project spark-failure-with-sbt-run-build-build-build from metals.sbt ...
[info] loading project definition from /github.com/sammyne/spark-failure-with-sbt-run/project/project/project
[info] loading settings for project spark-failure-with-sbt-run-build-build from metals.sbt ...
[info] loading project definition from /github.com/sammyne/spark-failure-with-sbt-run/project/project
[success] Generated .bloop/spark-failure-with-sbt-run-build-build.json
[success] Total time: 0 s, completed Apr 27, 2022, 7:56:20 AM
[info] loading settings for project spark-failure-with-sbt-run-build from metals.sbt,plugins.sbt ...
[info] loading project definition from /github.com/sammyne/spark-failure-with-sbt-run/project
[success] Generated .bloop/spark-failure-with-sbt-run-build.json
[success] Total time: 0 s, completed Apr 27, 2022, 7:56:20 AM
[info] loading settings for project spark-failure-with-sbt-run from build.sbt ...
[info] set current project to hello-world (in build file:/github.com/sammyne/spark-failure-with-sbt-run/)
[info] running Main 
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.apache.spark.unsafe.Platform (file:/github.com/sammyne/spark-failure-with-sbt-run/target/bg-jobs/sbt_b7a00768/target/e6cc3437/08fe7b74/spark-unsafe_2.13-3.2.1.jar) to constructor java.nio.DirectByteBuffer(long,int)
WARNING: Please consider reporting this to the maintainers of org.apache.spark.unsafe.Platform
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
22/04/27 07:56:22 INFO SparkContext: Running Spark version 3.2.1
22/04/27 07:56:22 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
22/04/27 07:56:22 INFO ResourceUtils: ==============================================================
22/04/27 07:56:22 INFO ResourceUtils: No custom resources configured for spark.driver.
22/04/27 07:56:22 INFO ResourceUtils: ==============================================================
22/04/27 07:56:22 INFO SparkContext: Submitted application: CSV to Dataset
22/04/27 07:56:22 INFO ResourceProfile: Default ResourceProfile created, executor resources: Map(cores -> name: cores, amount: 1, script: , vendor: , memory -> name: memory, amount: 1024, script: , vendor: , offHeap -> name: offHeap, amount: 0, script: , vendor: ), task resources: Map(cpus -> name: cpus, amount: 1.0)
22/04/27 07:56:22 INFO ResourceProfile: Limiting resource is cpu
22/04/27 07:56:22 INFO ResourceProfileManager: Added ResourceProfile id: 0
22/04/27 07:56:22 INFO SecurityManager: Changing view acls to: root
22/04/27 07:56:22 INFO SecurityManager: Changing modify acls to: root
22/04/27 07:56:22 INFO SecurityManager: Changing view acls groups to: 
22/04/27 07:56:22 INFO SecurityManager: Changing modify acls groups to: 
22/04/27 07:56:22 INFO SecurityManager: SecurityManager: authentication disabled; ui acls disabled; users  with view permissions: Set(root); groups with view permissions: Set(); users  with modify permissions: Set(root); groups with modify permissions: Set()
22/04/27 07:56:22 INFO Utils: Successfully started service 'sparkDriver' on port 43659.
22/04/27 07:56:22 INFO SparkEnv: Registering MapOutputTracker
22/04/27 07:56:22 INFO SparkEnv: Registering BlockManagerMaster
22/04/27 07:56:22 INFO BlockManagerMasterEndpoint: Using org.apache.spark.storage.DefaultTopologyMapper for getting topology information
22/04/27 07:56:22 INFO BlockManagerMasterEndpoint: BlockManagerMasterEndpoint up
22/04/27 07:56:22 INFO SparkEnv: Registering BlockManagerMasterHeartbeat
22/04/27 07:56:22 INFO DiskBlockManager: Created local directory at /tmp/blockmgr-ee687936-a8e0-4576-9896-b97b5a86a920
22/04/27 07:56:22 INFO MemoryStore: MemoryStore started with capacity 434.4 MiB
22/04/27 07:56:22 INFO SparkEnv: Registering OutputCommitCoordinator
22/04/27 07:56:22 INFO Utils: Successfully started service 'SparkUI' on port 4040.
22/04/27 07:56:22 INFO SparkUI: Bound SparkUI to 0.0.0.0, and started at http://5f46726b8883:4040
22/04/27 07:56:22 INFO Executor: Starting executor ID driver on host 5f46726b8883
22/04/27 07:56:23 INFO Utils: Successfully started service 'org.apache.spark.network.netty.NettyBlockTransferService' on port 43389.
22/04/27 07:56:23 INFO NettyBlockTransferService: Server created on 5f46726b8883:43389
22/04/27 07:56:23 INFO BlockManager: Using org.apache.spark.storage.RandomBlockReplicationPolicy for block replication policy
22/04/27 07:56:23 INFO BlockManagerMaster: Registering BlockManager BlockManagerId(driver, 5f46726b8883, 43389, None)
22/04/27 07:56:23 INFO BlockManagerMasterEndpoint: Registering block manager 5f46726b8883:43389 with 434.4 MiB RAM, BlockManagerId(driver, 5f46726b8883, 43389, None)
22/04/27 07:56:23 INFO BlockManagerMaster: Registered BlockManager BlockManagerId(driver, 5f46726b8883, 43389, None)
22/04/27 07:56:23 INFO BlockManager: Initialized BlockManager: BlockManagerId(driver, 5f46726b8883, 43389, None)
22/04/27 07:56:23 INFO SharedState: Setting hive.metastore.warehouse.dir ('null') to the value of spark.sql.warehouse.dir.
22/04/27 07:56:23 INFO SharedState: Warehouse path is 'file:/github.com/sammyne/spark-failure-with-sbt-run/spark-warehouse'.
22/04/27 07:56:24 INFO InMemoryFileIndex: It took 31 ms to list leaf files for 1 paths.
22/04/27 07:56:24 INFO InMemoryFileIndex: It took 1 ms to list leaf files for 1 paths.
22/04/27 07:56:25 INFO FileSourceStrategy: Pushed Filters: 
22/04/27 07:56:25 INFO FileSourceStrategy: Post-Scan Filters: (length(trim(value#0, None)) > 0)
22/04/27 07:56:25 INFO FileSourceStrategy: Output Data Schema: struct<value: string>
22/04/27 07:56:26 INFO CodeGenerator: Code generated in 165.514785 ms
22/04/27 07:56:26 INFO MemoryStore: Block broadcast_0 stored as values in memory (estimated size 189.4 KiB, free 434.2 MiB)
22/04/27 07:56:26 INFO MemoryStore: Block broadcast_0_piece0 stored as bytes in memory (estimated size 32.7 KiB, free 434.2 MiB)
22/04/27 07:56:26 INFO BlockManagerInfo: Added broadcast_0_piece0 in memory on 5f46726b8883:43389 (size: 32.7 KiB, free: 434.4 MiB)
22/04/27 07:56:26 INFO SparkContext: Created broadcast 0 from load at Main.scala:14
22/04/27 07:56:26 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4196197 bytes, open cost is considered as scanning 4194304 bytes.
22/04/27 07:56:26 INFO SparkContext: Starting job: load at Main.scala:14
22/04/27 07:56:26 INFO DAGScheduler: Got job 0 (load at Main.scala:14) with 1 output partitions
22/04/27 07:56:26 INFO DAGScheduler: Final stage: ResultStage 0 (load at Main.scala:14)
22/04/27 07:56:26 INFO DAGScheduler: Parents of final stage: List()
22/04/27 07:56:26 INFO DAGScheduler: Missing parents: List()
22/04/27 07:56:26 INFO DAGScheduler: Submitting ResultStage 0 (MapPartitionsRDD[3] at load at Main.scala:14), which has no missing parents
22/04/27 07:56:26 INFO MemoryStore: Block broadcast_1 stored as values in memory (estimated size 11.9 KiB, free 434.2 MiB)
22/04/27 07:56:26 INFO MemoryStore: Block broadcast_1_piece0 stored as bytes in memory (estimated size 5.9 KiB, free 434.2 MiB)
22/04/27 07:56:26 INFO BlockManagerInfo: Added broadcast_1_piece0 in memory on 5f46726b8883:43389 (size: 5.9 KiB, free: 434.4 MiB)
22/04/27 07:56:26 INFO SparkContext: Created broadcast 1 from broadcast at DAGScheduler.scala:1478
22/04/27 07:56:26 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 0 (MapPartitionsRDD[3] at load at Main.scala:14) (first 15 tasks are for partitions Vector(0))
22/04/27 07:56:26 INFO TaskSchedulerImpl: Adding task set 0.0 with 1 tasks resource profile 0
22/04/27 07:56:26 INFO TaskSetManager: Starting task 0.0 in stage 0.0 (TID 0) (5f46726b8883, executor driver, partition 0, PROCESS_LOCAL, 7843 bytes) taskResourceAssignments Map()
22/04/27 07:56:26 INFO Executor: Running task 0.0 in stage 0.0 (TID 0)
22/04/27 07:56:26 INFO FileScanRDD: Reading File path: file:///github.com/sammyne/spark-failure-with-sbt-run/testdata/books.csv, range: 0-1893, partition values: [empty row]
22/04/27 07:56:26 INFO CodeGenerator: Code generated in 11.615393 ms
22/04/27 07:56:26 INFO Executor: Finished task 0.0 in stage 0.0 (TID 0). 1639 bytes result sent to driver
22/04/27 07:56:26 INFO TaskSetManager: Finished task 0.0 in stage 0.0 (TID 0) in 188 ms on 5f46726b8883 (executor driver) (1/1)
22/04/27 07:56:26 INFO TaskSchedulerImpl: Removed TaskSet 0.0, whose tasks have all completed, from pool 
22/04/27 07:56:26 INFO DAGScheduler: ResultStage 0 (load at Main.scala:14) finished in 0.283 s
22/04/27 07:56:26 INFO DAGScheduler: Job 0 is finished. Cancelling potential speculative or zombie tasks for this job
22/04/27 07:56:26 INFO TaskSchedulerImpl: Killing all running tasks in stage 0: Stage finished
22/04/27 07:56:26 INFO DAGScheduler: Job 0 finished: load at Main.scala:14, took 0.312794 s
22/04/27 07:56:26 INFO CodeGenerator: Code generated in 7.909508 ms
22/04/27 07:56:26 INFO FileSourceStrategy: Pushed Filters: 
22/04/27 07:56:26 INFO FileSourceStrategy: Post-Scan Filters: 
22/04/27 07:56:26 INFO FileSourceStrategy: Output Data Schema: struct<value: string>
22/04/27 07:56:26 INFO MemoryStore: Block broadcast_2 stored as values in memory (estimated size 189.4 KiB, free 434.0 MiB)
22/04/27 07:56:26 INFO MemoryStore: Block broadcast_2_piece0 stored as bytes in memory (estimated size 32.7 KiB, free 433.9 MiB)
22/04/27 07:56:26 INFO BlockManagerInfo: Added broadcast_2_piece0 in memory on 5f46726b8883:43389 (size: 32.7 KiB, free: 434.3 MiB)
22/04/27 07:56:26 INFO SparkContext: Created broadcast 2 from load at Main.scala:14
22/04/27 07:56:26 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4196197 bytes, open cost is considered as scanning 4194304 bytes.
22/04/27 07:56:26 INFO FileSourceStrategy: Pushed Filters: 
22/04/27 07:56:26 INFO FileSourceStrategy: Post-Scan Filters: 
22/04/27 07:56:26 INFO FileSourceStrategy: Output Data Schema: struct<id: string, authorId: string, title: string, releaseDate: string, link: string ... 3 more fields>
22/04/27 07:56:26 INFO MemoryStore: Block broadcast_3 stored as values in memory (estimated size 189.3 KiB, free 433.8 MiB)
22/04/27 07:56:26 INFO MemoryStore: Block broadcast_3_piece0 stored as bytes in memory (estimated size 32.6 KiB, free 433.7 MiB)
22/04/27 07:56:26 INFO BlockManagerInfo: Added broadcast_3_piece0 in memory on 5f46726b8883:43389 (size: 32.6 KiB, free: 434.3 MiB)
22/04/27 07:56:26 INFO SparkContext: Created broadcast 3 from show at Main.scala:16
22/04/27 07:56:26 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4196197 bytes, open cost is considered as scanning 4194304 bytes.
22/04/27 07:56:26 INFO SparkContext: Starting job: show at Main.scala:16
22/04/27 07:56:26 INFO DAGScheduler: Got job 1 (show at Main.scala:16) with 1 output partitions
22/04/27 07:56:26 INFO DAGScheduler: Final stage: ResultStage 1 (show at Main.scala:16)
22/04/27 07:56:26 INFO DAGScheduler: Parents of final stage: List()
22/04/27 07:56:26 INFO DAGScheduler: Missing parents: List()
22/04/27 07:56:26 INFO DAGScheduler: Submitting ResultStage 1 (MapPartitionsRDD[12] at show at Main.scala:16), which has no missing parents
22/04/27 07:56:26 INFO MemoryStore: Block broadcast_4 stored as values in memory (estimated size 10.4 KiB, free 433.7 MiB)
22/04/27 07:56:26 INFO MemoryStore: Block broadcast_4_piece0 stored as bytes in memory (estimated size 5.6 KiB, free 433.7 MiB)
22/04/27 07:56:26 INFO BlockManagerInfo: Added broadcast_4_piece0 in memory on 5f46726b8883:43389 (size: 5.6 KiB, free: 434.3 MiB)
22/04/27 07:56:26 INFO SparkContext: Created broadcast 4 from broadcast at DAGScheduler.scala:1478
22/04/27 07:56:26 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 1 (MapPartitionsRDD[12] at show at Main.scala:16) (first 15 tasks are for partitions Vector(0))
22/04/27 07:56:26 INFO TaskSchedulerImpl: Adding task set 1.0 with 1 tasks resource profile 0
22/04/27 07:56:26 INFO TaskSetManager: Starting task 0.0 in stage 1.0 (TID 1) (5f46726b8883, executor driver, partition 0, PROCESS_LOCAL, 7843 bytes) taskResourceAssignments Map()
22/04/27 07:56:26 INFO Executor: Running task 0.0 in stage 1.0 (TID 1)
22/04/27 07:56:26 INFO FileScanRDD: Reading File path: file:///github.com/sammyne/spark-failure-with-sbt-run/testdata/books.csv, range: 0-1893, partition values: [empty row]
22/04/27 07:56:26 INFO CodeGenerator: Code generated in 11.467536 ms
22/04/27 07:56:26 INFO Executor: Finished task 0.0 in stage 1.0 (TID 1). 2196 bytes result sent to driver
22/04/27 07:56:26 INFO TaskSetManager: Finished task 0.0 in stage 1.0 (TID 1) in 49 ms on 5f46726b8883 (executor driver) (1/1)
22/04/27 07:56:26 INFO TaskSchedulerImpl: Removed TaskSet 1.0, whose tasks have all completed, from pool 
22/04/27 07:56:26 INFO DAGScheduler: ResultStage 1 (show at Main.scala:16) finished in 0.061 s
22/04/27 07:56:26 INFO DAGScheduler: Job 1 is finished. Cancelling potential speculative or zombie tasks for this job
22/04/27 07:56:26 INFO TaskSchedulerImpl: Killing all running tasks in stage 1: Stage finished
22/04/27 07:56:26 INFO DAGScheduler: Job 1 finished: show at Main.scala:16, took 0.063674 s
22/04/27 07:56:26 INFO CodeGenerator: Code generated in 16.313 ms
+---+--------+--------------------+-----------+--------------------+
| id|authorId|               title|releaseDate|                link|
+---+--------+--------------------+-----------+--------------------+
|  1|       1|Fantastic Beasts ...|   11/18/16|http://amzn.to/2k...|
|  2|       1|Harry Potter and ...|    10/6/15|http://amzn.to/2l...|
|  3|       1|The Tales of Beed...|    12/4/08|http://amzn.to/2k...|
|  4|       1|Harry Potter and ...|    10/4/16|http://amzn.to/2k...|
|  5|       2|Informix 12.10 on...|    4/23/17|http://amzn.to/2i...|
+---+--------+--------------------+-----------+--------------------+
only showing top 5 rows

22/04/27 07:56:27 INFO SparkUI: Stopped Spark web UI at http://5f46726b8883:4040
22/04/27 07:56:27 INFO MapOutputTrackerMasterEndpoint: MapOutputTrackerMasterEndpoint stopped!
22/04/27 07:56:27 INFO MemoryStore: MemoryStore cleared
22/04/27 07:56:27 INFO BlockManager: BlockManager stopped
22/04/27 07:56:27 INFO BlockManagerMaster: BlockManagerMaster stopped
22/04/27 07:56:27 INFO OutputCommitCoordinator$OutputCommitCoordinatorEndpoint: OutputCommitCoordinator stopped!
22/04/27 07:56:27 INFO SparkContext: Successfully stopped SparkContext
[success] Total time: 6 s, completed Apr 27, 2022, 7:56:27 AM
22/04/27 07:56:27 INFO ShutdownHookManager: Shutdown hook called
22/04/27 07:56:27 INFO ShutdownHookManager: Deleting directory /tmp/spark-e335afa8-1c86-4100-892f-6e5801079d0e
22/04/27 07:56:27 ERROR Configuration: error parsing conf core-default.xml
java.nio.file.NoSuchFileException: /github.com/sammyne/spark-failure-with-sbt-run/target/bg-jobs/sbt_b7a00768/target/2ab34e8d/81ecd14d/hadoop-client-api-3.3.1.jar
        at java.base/sun.nio.fs.UnixException.translateToIOException(UnixException.java:92)
        at java.base/sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:111)
        at java.base/sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:116)
        at java.base/sun.nio.fs.UnixFileAttributeViews$Basic.readAttributes(UnixFileAttributeViews.java:55)
        at java.base/sun.nio.fs.UnixFileSystemProvider.readAttributes(UnixFileSystemProvider.java:145)
        at java.base/sun.nio.fs.LinuxFileSystemProvider.readAttributes(LinuxFileSystemProvider.java:99)
        at java.base/java.nio.file.Files.readAttributes(Files.java:1763)
        at java.base/java.util.zip.ZipFile$Source.get(ZipFile.java:1222)
        at java.base/java.util.zip.ZipFile$CleanableResource.<init>(ZipFile.java:824)
        at java.base/java.util.zip.ZipFile$CleanableResource$FinalizableResource.<init>(ZipFile.java:850)
        at java.base/java.util.zip.ZipFile$CleanableResource.get(ZipFile.java:839)
        at java.base/java.util.zip.ZipFile.<init>(ZipFile.java:246)
        at java.base/java.util.zip.ZipFile.<init>(ZipFile.java:176)
        at java.base/java.util.jar.JarFile.<init>(JarFile.java:346)
        at java.base/sun.net.www.protocol.jar.URLJarFile.<init>(URLJarFile.java:103)
        at java.base/sun.net.www.protocol.jar.URLJarFile.getJarFile(URLJarFile.java:72)
        at java.base/sun.net.www.protocol.jar.JarFileFactory.get(JarFileFactory.java:99)
        at java.base/sun.net.www.protocol.jar.JarURLConnection.connect(JarURLConnection.java:125)
        at java.base/sun.net.www.protocol.jar.JarURLConnection.getInputStream(JarURLConnection.java:155)
        at org.apache.hadoop.conf.Configuration.parse(Configuration.java:2986)
        at org.apache.hadoop.conf.Configuration.getStreamReader(Configuration.java:3082)
        at org.apache.hadoop.conf.Configuration.loadResource(Configuration.java:3040)
        at org.apache.hadoop.conf.Configuration.loadResources(Configuration.java:3013)
        at org.apache.hadoop.conf.Configuration.loadProps(Configuration.java:2893)
        at org.apache.hadoop.conf.Configuration.getProps(Configuration.java:2875)
        at org.apache.hadoop.conf.Configuration.get(Configuration.java:1225)
        at org.apache.hadoop.conf.Configuration.getTimeDuration(Configuration.java:1842)
        at org.apache.hadoop.conf.Configuration.getTimeDuration(Configuration.java:1819)
        at org.apache.hadoop.util.ShutdownHookManager.getShutdownTimeout(ShutdownHookManager.java:183)
        at org.apache.hadoop.util.ShutdownHookManager.shutdownExecutor(ShutdownHookManager.java:145)
        at org.apache.hadoop.util.ShutdownHookManager.access$300(ShutdownHookManager.java:65)
        at org.apache.hadoop.util.ShutdownHookManager$1.run(ShutdownHookManager.java:102)
Exception in thread "Thread-2" java.lang.RuntimeException: java.nio.file.NoSuchFileException: /github.com/sammyne/spark-failure-with-sbt-run/target/bg-jobs/sbt_b7a00768/target/2ab34e8d/81ecd14d/hadoop-client-api-3.3.1.jar
        at org.apache.hadoop.conf.Configuration.loadResource(Configuration.java:3066)
        at org.apache.hadoop.conf.Configuration.loadResources(Configuration.java:3013)
        at org.apache.hadoop.conf.Configuration.loadProps(Configuration.java:2893)
        at org.apache.hadoop.conf.Configuration.getProps(Configuration.java:2875)
        at org.apache.hadoop.conf.Configuration.get(Configuration.java:1225)
        at org.apache.hadoop.conf.Configuration.getTimeDuration(Configuration.java:1842)
        at org.apache.hadoop.conf.Configuration.getTimeDuration(Configuration.java:1819)
        at org.apache.hadoop.util.ShutdownHookManager.getShutdownTimeout(ShutdownHookManager.java:183)
        at org.apache.hadoop.util.ShutdownHookManager.shutdownExecutor(ShutdownHookManager.java:145)
        at org.apache.hadoop.util.ShutdownHookManager.access$300(ShutdownHookManager.java:65)
        at org.apache.hadoop.util.ShutdownHookManager$1.run(ShutdownHookManager.java:102)
Caused by: java.nio.file.NoSuchFileException: /github.com/sammyne/spark-failure-with-sbt-run/target/bg-jobs/sbt_b7a00768/target/2ab34e8d/81ecd14d/hadoop-client-api-3.3.1.jar
        at java.base/sun.nio.fs.UnixException.translateToIOException(UnixException.java:92)
        at java.base/sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:111)
        at java.base/sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:116)
        at java.base/sun.nio.fs.UnixFileAttributeViews$Basic.readAttributes(UnixFileAttributeViews.java:55)
        at java.base/sun.nio.fs.UnixFileSystemProvider.readAttributes(UnixFileSystemProvider.java:145)
        at java.base/sun.nio.fs.LinuxFileSystemProvider.readAttributes(LinuxFileSystemProvider.java:99)
        at java.base/java.nio.file.Files.readAttributes(Files.java:1763)
        at java.base/java.util.zip.ZipFile$Source.get(ZipFile.java:1222)
        at java.base/java.util.zip.ZipFile$CleanableResource.<init>(ZipFile.java:824)
        at java.base/java.util.zip.ZipFile$CleanableResource$FinalizableResource.<init>(ZipFile.java:850)
        at java.base/java.util.zip.ZipFile$CleanableResource.get(ZipFile.java:839)
        at java.base/java.util.zip.ZipFile.<init>(ZipFile.java:246)
        at java.base/java.util.zip.ZipFile.<init>(ZipFile.java:176)
        at java.base/java.util.jar.JarFile.<init>(JarFile.java:346)
        at java.base/sun.net.www.protocol.jar.URLJarFile.<init>(URLJarFile.java:103)
        at java.base/sun.net.www.protocol.jar.URLJarFile.getJarFile(URLJarFile.java:72)
        at java.base/sun.net.www.protocol.jar.JarFileFactory.get(JarFileFactory.java:99)
        at java.base/sun.net.www.protocol.jar.JarURLConnection.connect(JarURLConnection.java:125)
        at java.base/sun.net.www.protocol.jar.JarURLConnection.getInputStream(JarURLConnection.java:155)
        at org.apache.hadoop.conf.Configuration.parse(Configuration.java:2986)
        at org.apache.hadoop.conf.Configuration.getStreamReader(Configuration.java:3082)
        at org.apache.hadoop.conf.Configuration.loadResource(Configuration.java:3040)
        ... 10 more
```

### `sbt` and then `run`

```bash
sbt

# after entering the sbt shell
run
```

At this moment, it's fine with logs as

```bash
[info] running Main 
WARNING: An illegal reflective access operation has occurred
WARNING: Illegal reflective access by org.apache.spark.unsafe.Platform (file:/github.com/sammyne/spark-failure-with-sbt-run/target/bg-jobs/sbt_28d6c4e/target/e6cc3437/08fe7b74/spark-unsafe_2.13-3.2.1.jar) to constructor java.nio.DirectByteBuffer(long,int)
WARNING: Please consider reporting this to the maintainers of org.apache.spark.unsafe.Platform
WARNING: Use --illegal-access=warn to enable warnings of further illegal reflective access operations
WARNING: All illegal access operations will be denied in a future release
Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
22/04/27 07:51:55 INFO SparkContext: Running Spark version 3.2.1
22/04/27 07:51:55 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
22/04/27 07:51:55 INFO ResourceUtils: ==============================================================
22/04/27 07:51:55 INFO ResourceUtils: No custom resources configured for spark.driver.
22/04/27 07:51:55 INFO ResourceUtils: ==============================================================
22/04/27 07:51:55 INFO SparkContext: Submitted application: CSV to Dataset
22/04/27 07:51:55 INFO ResourceProfile: Default ResourceProfile created, executor resources: Map(cores -> name: cores, amount: 1, script: , vendor: , memory -> name: memory, amount: 1024, script: , vendor: , offHeap -> name: offHeap, amount: 0, script: , vendor: ), task resources: Map(cpus -> name: cpus, amount: 1.0)
22/04/27 07:51:55 INFO ResourceProfile: Limiting resource is cpu
22/04/27 07:51:55 INFO ResourceProfileManager: Added ResourceProfile id: 0
22/04/27 07:51:55 INFO SecurityManager: Changing view acls to: root
22/04/27 07:51:55 INFO SecurityManager: Changing modify acls to: root
22/04/27 07:51:55 INFO SecurityManager: Changing view acls groups to: 
22/04/27 07:51:55 INFO SecurityManager: Changing modify acls groups to: 
22/04/27 07:51:55 INFO SecurityManager: SecurityManager: authentication disabled; ui acls disabled; users  with view permissions: Set(root); groups with view permissions: Set(); users  with modify permissions: Set(root); groups with modify permissions: Set()
22/04/27 07:51:56 INFO Utils: Successfully started service 'sparkDriver' on port 45473.
22/04/27 07:51:56 INFO SparkEnv: Registering MapOutputTracker
22/04/27 07:51:56 INFO SparkEnv: Registering BlockManagerMaster
22/04/27 07:51:56 INFO BlockManagerMasterEndpoint: Using org.apache.spark.storage.DefaultTopologyMapper for getting topology information
22/04/27 07:51:56 INFO BlockManagerMasterEndpoint: BlockManagerMasterEndpoint up
22/04/27 07:51:56 INFO SparkEnv: Registering BlockManagerMasterHeartbeat
22/04/27 07:51:56 INFO DiskBlockManager: Created local directory at /tmp/blockmgr-72993298-f4b5-4bbb-b442-9da8638b2675
22/04/27 07:51:56 INFO MemoryStore: MemoryStore started with capacity 434.4 MiB
22/04/27 07:51:56 INFO SparkEnv: Registering OutputCommitCoordinator
22/04/27 07:51:56 INFO Utils: Successfully started service 'SparkUI' on port 4040.
22/04/27 07:51:56 INFO SparkUI: Bound SparkUI to 0.0.0.0, and started at http://5f46726b8883:4040
22/04/27 07:51:56 INFO Executor: Starting executor ID driver on host 5f46726b8883
22/04/27 07:51:56 INFO Utils: Successfully started service 'org.apache.spark.network.netty.NettyBlockTransferService' on port 42221.
22/04/27 07:51:56 INFO NettyBlockTransferService: Server created on 5f46726b8883:42221
22/04/27 07:51:56 INFO BlockManager: Using org.apache.spark.storage.RandomBlockReplicationPolicy for block replication policy
22/04/27 07:51:56 INFO BlockManagerMaster: Registering BlockManager BlockManagerId(driver, 5f46726b8883, 42221, None)
22/04/27 07:51:56 INFO BlockManagerMasterEndpoint: Registering block manager 5f46726b8883:42221 with 434.4 MiB RAM, BlockManagerId(driver, 5f46726b8883, 42221, None)
22/04/27 07:51:56 INFO BlockManagerMaster: Registered BlockManager BlockManagerId(driver, 5f46726b8883, 42221, None)
22/04/27 07:51:56 INFO BlockManager: Initialized BlockManager: BlockManagerId(driver, 5f46726b8883, 42221, None)
22/04/27 07:51:56 INFO SharedState: Setting hive.metastore.warehouse.dir ('null') to the value of spark.sql.warehouse.dir.
22/04/27 07:51:56 INFO SharedState: Warehouse path is 'file:/github.com/sammyne/spark-failure-with-sbt-run/spark-warehouse'.
22/04/27 07:51:57 INFO InMemoryFileIndex: It took 32 ms to list leaf files for 1 paths.
22/04/27 07:51:57 INFO InMemoryFileIndex: It took 1 ms to list leaf files for 1 paths.
22/04/27 07:51:59 INFO FileSourceStrategy: Pushed Filters: 
22/04/27 07:51:59 INFO FileSourceStrategy: Post-Scan Filters: (length(trim(value#0, None)) > 0)
22/04/27 07:51:59 INFO FileSourceStrategy: Output Data Schema: struct<value: string>
22/04/27 07:51:59 INFO CodeGenerator: Code generated in 157.373812 ms
22/04/27 07:51:59 INFO MemoryStore: Block broadcast_0 stored as values in memory (estimated size 189.4 KiB, free 434.2 MiB)
22/04/27 07:51:59 INFO MemoryStore: Block broadcast_0_piece0 stored as bytes in memory (estimated size 32.7 KiB, free 434.2 MiB)
22/04/27 07:51:59 INFO BlockManagerInfo: Added broadcast_0_piece0 in memory on 5f46726b8883:42221 (size: 32.7 KiB, free: 434.4 MiB)
22/04/27 07:51:59 INFO SparkContext: Created broadcast 0 from load at Main.scala:14
22/04/27 07:51:59 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4196197 bytes, open cost is considered as scanning 4194304 bytes.
22/04/27 07:51:59 INFO SparkContext: Starting job: load at Main.scala:14
22/04/27 07:52:00 INFO DAGScheduler: Got job 0 (load at Main.scala:14) with 1 output partitions
22/04/27 07:52:00 INFO DAGScheduler: Final stage: ResultStage 0 (load at Main.scala:14)
22/04/27 07:52:00 INFO DAGScheduler: Parents of final stage: List()
22/04/27 07:52:00 INFO DAGScheduler: Missing parents: List()
22/04/27 07:52:00 INFO DAGScheduler: Submitting ResultStage 0 (MapPartitionsRDD[3] at load at Main.scala:14), which has no missing parents
22/04/27 07:52:00 INFO MemoryStore: Block broadcast_1 stored as values in memory (estimated size 11.9 KiB, free 434.2 MiB)
22/04/27 07:52:00 INFO MemoryStore: Block broadcast_1_piece0 stored as bytes in memory (estimated size 5.9 KiB, free 434.2 MiB)
22/04/27 07:52:00 INFO BlockManagerInfo: Added broadcast_1_piece0 in memory on 5f46726b8883:42221 (size: 5.9 KiB, free: 434.4 MiB)
22/04/27 07:52:00 INFO SparkContext: Created broadcast 1 from broadcast at DAGScheduler.scala:1478
22/04/27 07:52:00 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 0 (MapPartitionsRDD[3] at load at Main.scala:14) (first 15 tasks are for partitions Vector(0))
22/04/27 07:52:00 INFO TaskSchedulerImpl: Adding task set 0.0 with 1 tasks resource profile 0
22/04/27 07:52:00 INFO TaskSetManager: Starting task 0.0 in stage 0.0 (TID 0) (5f46726b8883, executor driver, partition 0, PROCESS_LOCAL, 7843 bytes) taskResourceAssignments Map()
22/04/27 07:52:00 INFO Executor: Running task 0.0 in stage 0.0 (TID 0)
22/04/27 07:52:00 INFO FileScanRDD: Reading File path: file:///github.com/sammyne/spark-failure-with-sbt-run/testdata/books.csv, range: 0-1893, partition values: [empty row]
22/04/27 07:52:00 INFO CodeGenerator: Code generated in 11.921485 ms
22/04/27 07:52:00 INFO Executor: Finished task 0.0 in stage 0.0 (TID 0). 1639 bytes result sent to driver
22/04/27 07:52:00 INFO TaskSetManager: Finished task 0.0 in stage 0.0 (TID 0) in 205 ms on 5f46726b8883 (executor driver) (1/1)
22/04/27 07:52:00 INFO TaskSchedulerImpl: Removed TaskSet 0.0, whose tasks have all completed, from pool 
22/04/27 07:52:00 INFO DAGScheduler: ResultStage 0 (load at Main.scala:14) finished in 0.310 s
22/04/27 07:52:00 INFO DAGScheduler: Job 0 is finished. Cancelling potential speculative or zombie tasks for this job
22/04/27 07:52:00 INFO TaskSchedulerImpl: Killing all running tasks in stage 0: Stage finished
22/04/27 07:52:00 INFO DAGScheduler: Job 0 finished: load at Main.scala:14, took 0.343392 s
22/04/27 07:52:00 INFO CodeGenerator: Code generated in 8.079927 ms
22/04/27 07:52:00 INFO FileSourceStrategy: Pushed Filters: 
22/04/27 07:52:00 INFO FileSourceStrategy: Post-Scan Filters: 
22/04/27 07:52:00 INFO FileSourceStrategy: Output Data Schema: struct<value: string>
22/04/27 07:52:00 INFO MemoryStore: Block broadcast_2 stored as values in memory (estimated size 189.4 KiB, free 434.0 MiB)
22/04/27 07:52:00 INFO MemoryStore: Block broadcast_2_piece0 stored as bytes in memory (estimated size 32.7 KiB, free 433.9 MiB)
22/04/27 07:52:00 INFO BlockManagerInfo: Added broadcast_2_piece0 in memory on 5f46726b8883:42221 (size: 32.7 KiB, free: 434.3 MiB)
22/04/27 07:52:00 INFO SparkContext: Created broadcast 2 from load at Main.scala:14
22/04/27 07:52:00 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4196197 bytes, open cost is considered as scanning 4194304 bytes.
22/04/27 07:52:00 INFO FileSourceStrategy: Pushed Filters: 
22/04/27 07:52:00 INFO FileSourceStrategy: Post-Scan Filters: 
22/04/27 07:52:00 INFO FileSourceStrategy: Output Data Schema: struct<id: string, authorId: string, title: string, releaseDate: string, link: string ... 3 more fields>
22/04/27 07:52:00 INFO MemoryStore: Block broadcast_3 stored as values in memory (estimated size 189.3 KiB, free 433.8 MiB)
22/04/27 07:52:00 INFO MemoryStore: Block broadcast_3_piece0 stored as bytes in memory (estimated size 32.6 KiB, free 433.7 MiB)
22/04/27 07:52:00 INFO BlockManagerInfo: Added broadcast_3_piece0 in memory on 5f46726b8883:42221 (size: 32.6 KiB, free: 434.3 MiB)
22/04/27 07:52:00 INFO SparkContext: Created broadcast 3 from show at Main.scala:16
22/04/27 07:52:00 INFO FileSourceScanExec: Planning scan with bin packing, max size: 4196197 bytes, open cost is considered as scanning 4194304 bytes.
22/04/27 07:52:00 INFO SparkContext: Starting job: show at Main.scala:16
22/04/27 07:52:00 INFO DAGScheduler: Got job 1 (show at Main.scala:16) with 1 output partitions
22/04/27 07:52:00 INFO DAGScheduler: Final stage: ResultStage 1 (show at Main.scala:16)
22/04/27 07:52:00 INFO DAGScheduler: Parents of final stage: List()
22/04/27 07:52:00 INFO DAGScheduler: Missing parents: List()
22/04/27 07:52:00 INFO DAGScheduler: Submitting ResultStage 1 (MapPartitionsRDD[12] at show at Main.scala:16), which has no missing parents
22/04/27 07:52:00 INFO MemoryStore: Block broadcast_4 stored as values in memory (estimated size 10.4 KiB, free 433.7 MiB)
22/04/27 07:52:00 INFO MemoryStore: Block broadcast_4_piece0 stored as bytes in memory (estimated size 5.7 KiB, free 433.7 MiB)
22/04/27 07:52:00 INFO BlockManagerInfo: Added broadcast_4_piece0 in memory on 5f46726b8883:42221 (size: 5.7 KiB, free: 434.3 MiB)
22/04/27 07:52:00 INFO SparkContext: Created broadcast 4 from broadcast at DAGScheduler.scala:1478
22/04/27 07:52:00 INFO DAGScheduler: Submitting 1 missing tasks from ResultStage 1 (MapPartitionsRDD[12] at show at Main.scala:16) (first 15 tasks are for partitions Vector(0))
22/04/27 07:52:00 INFO TaskSchedulerImpl: Adding task set 1.0 with 1 tasks resource profile 0
22/04/27 07:52:00 INFO TaskSetManager: Starting task 0.0 in stage 1.0 (TID 1) (5f46726b8883, executor driver, partition 0, PROCESS_LOCAL, 7843 bytes) taskResourceAssignments Map()
22/04/27 07:52:00 INFO Executor: Running task 0.0 in stage 1.0 (TID 1)
22/04/27 07:52:00 INFO FileScanRDD: Reading File path: file:///github.com/sammyne/spark-failure-with-sbt-run/testdata/books.csv, range: 0-1893, partition values: [empty row]
22/04/27 07:52:00 INFO CodeGenerator: Code generated in 11.294011 ms
22/04/27 07:52:00 INFO Executor: Finished task 0.0 in stage 1.0 (TID 1). 2196 bytes result sent to driver
22/04/27 07:52:00 INFO TaskSetManager: Finished task 0.0 in stage 1.0 (TID 1) in 45 ms on 5f46726b8883 (executor driver) (1/1)
22/04/27 07:52:00 INFO TaskSchedulerImpl: Removed TaskSet 1.0, whose tasks have all completed, from pool 
22/04/27 07:52:00 INFO DAGScheduler: ResultStage 1 (show at Main.scala:16) finished in 0.057 s
22/04/27 07:52:00 INFO DAGScheduler: Job 1 is finished. Cancelling potential speculative or zombie tasks for this job
22/04/27 07:52:00 INFO TaskSchedulerImpl: Killing all running tasks in stage 1: Stage finished
22/04/27 07:52:00 INFO DAGScheduler: Job 1 finished: show at Main.scala:16, took 0.061046 s
22/04/27 07:52:00 INFO CodeGenerator: Code generated in 14.213683 ms
+---+--------+--------------------+-----------+--------------------+
| id|authorId|               title|releaseDate|                link|
+---+--------+--------------------+-----------+--------------------+
|  1|       1|Fantastic Beasts ...|   11/18/16|http://amzn.to/2k...|
|  2|       1|Harry Potter and ...|    10/6/15|http://amzn.to/2l...|
|  3|       1|The Tales of Beed...|    12/4/08|http://amzn.to/2k...|
|  4|       1|Harry Potter and ...|    10/4/16|http://amzn.to/2k...|
|  5|       2|Informix 12.10 on...|    4/23/17|http://amzn.to/2i...|
+---+--------+--------------------+-----------+--------------------+
only showing top 5 rows

22/04/27 07:52:00 INFO SparkUI: Stopped Spark web UI at http://5f46726b8883:4040
22/04/27 07:52:00 INFO MapOutputTrackerMasterEndpoint: MapOutputTrackerMasterEndpoint stopped!
22/04/27 07:52:00 INFO MemoryStore: MemoryStore cleared
22/04/27 07:52:00 INFO BlockManager: BlockManager stopped
22/04/27 07:52:00 INFO BlockManagerMaster: BlockManagerMaster stopped
22/04/27 07:52:00 INFO OutputCommitCoordinator$OutputCommitCoordinatorEndpoint: OutputCommitCoordinator stopped!
22/04/27 07:52:00 INFO SparkContext: Successfully stopped SparkContext
[success] Total time: 6 s, completed Apr 27, 2022, 7:52:00 AM
```

However, once exit the shell, I got

```bash
[info] shutting down sbt server
22/04/27 07:55:10 INFO ShutdownHookManager: Shutdown hook called
22/04/27 07:55:10 INFO ShutdownHookManager: Deleting directory /tmp/spark-f28ecf9a-e963-459f-b54e-f1e4825ba210
22/04/27 07:55:10 ERROR Configuration: error parsing conf core-default.xml
java.nio.file.NoSuchFileException: /github.com/sammyne/spark-failure-with-sbt-run/target/bg-jobs/sbt_28d6c4e/target/2ab34e8d/81ecd14d/hadoop-client-api-3.3.1.jar
        at java.base/sun.nio.fs.UnixException.translateToIOException(UnixException.java:92)
        at java.base/sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:111)
        at java.base/sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:116)
        at java.base/sun.nio.fs.UnixFileAttributeViews$Basic.readAttributes(UnixFileAttributeViews.java:55)
        at java.base/sun.nio.fs.UnixFileSystemProvider.readAttributes(UnixFileSystemProvider.java:145)
        at java.base/sun.nio.fs.LinuxFileSystemProvider.readAttributes(LinuxFileSystemProvider.java:99)
        at java.base/java.nio.file.Files.readAttributes(Files.java:1763)
        at java.base/java.util.zip.ZipFile$Source.get(ZipFile.java:1222)
        at java.base/java.util.zip.ZipFile$CleanableResource.<init>(ZipFile.java:824)
        at java.base/java.util.zip.ZipFile$CleanableResource$FinalizableResource.<init>(ZipFile.java:850)
        at java.base/java.util.zip.ZipFile$CleanableResource.get(ZipFile.java:839)
        at java.base/java.util.zip.ZipFile.<init>(ZipFile.java:246)
        at java.base/java.util.zip.ZipFile.<init>(ZipFile.java:176)
        at java.base/java.util.jar.JarFile.<init>(JarFile.java:346)
        at java.base/sun.net.www.protocol.jar.URLJarFile.<init>(URLJarFile.java:103)
        at java.base/sun.net.www.protocol.jar.URLJarFile.getJarFile(URLJarFile.java:72)
        at java.base/sun.net.www.protocol.jar.JarFileFactory.get(JarFileFactory.java:99)
        at java.base/sun.net.www.protocol.jar.JarURLConnection.connect(JarURLConnection.java:125)
        at java.base/sun.net.www.protocol.jar.JarURLConnection.getInputStream(JarURLConnection.java:155)
        at org.apache.hadoop.conf.Configuration.parse(Configuration.java:2986)
        at org.apache.hadoop.conf.Configuration.getStreamReader(Configuration.java:3082)
        at org.apache.hadoop.conf.Configuration.loadResource(Configuration.java:3040)
        at org.apache.hadoop.conf.Configuration.loadResources(Configuration.java:3013)
        at org.apache.hadoop.conf.Configuration.loadProps(Configuration.java:2893)
        at org.apache.hadoop.conf.Configuration.getProps(Configuration.java:2875)
        at org.apache.hadoop.conf.Configuration.get(Configuration.java:1225)
        at org.apache.hadoop.conf.Configuration.getTimeDuration(Configuration.java:1842)
        at org.apache.hadoop.conf.Configuration.getTimeDuration(Configuration.java:1819)
        at org.apache.hadoop.util.ShutdownHookManager.getShutdownTimeout(ShutdownHookManager.java:183)
        at org.apache.hadoop.util.ShutdownHookManager.shutdownExecutor(ShutdownHookManager.java:145)
        at org.apache.hadoop.util.ShutdownHookManager.access$300(ShutdownHookManager.java:65)
        at org.apache.hadoop.util.ShutdownHookManager$1.run(ShutdownHookManager.java:102)
Exception in thread "Thread-2" java.lang.RuntimeException: java.nio.file.NoSuchFileException: /github.com/sammyne/spark-failure-with-sbt-run/target/bg-jobs/sbt_28d6c4e/target/2ab34e8d/81ecd14d/hadoop-client-api-3.3.1.jar
        at org.apache.hadoop.conf.Configuration.loadResource(Configuration.java:3066)
        at org.apache.hadoop.conf.Configuration.loadResources(Configuration.java:3013)
        at org.apache.hadoop.conf.Configuration.loadProps(Configuration.java:2893)
        at org.apache.hadoop.conf.Configuration.getProps(Configuration.java:2875)
        at org.apache.hadoop.conf.Configuration.get(Configuration.java:1225)
        at org.apache.hadoop.conf.Configuration.getTimeDuration(Configuration.java:1842)
        at org.apache.hadoop.conf.Configuration.getTimeDuration(Configuration.java:1819)
        at org.apache.hadoop.util.ShutdownHookManager.getShutdownTimeout(ShutdownHookManager.java:183)
        at org.apache.hadoop.util.ShutdownHookManager.shutdownExecutor(ShutdownHookManager.java:145)
        at org.apache.hadoop.util.ShutdownHookManager.access$300(ShutdownHookManager.java:65)
        at org.apache.hadoop.util.ShutdownHookManager$1.run(ShutdownHookManager.java:102)
Caused by: java.nio.file.NoSuchFileException: /github.com/sammyne/spark-failure-with-sbt-run/target/bg-jobs/sbt_28d6c4e/target/2ab34e8d/81ecd14d/hadoop-client-api-3.3.1.jar
        at java.base/sun.nio.fs.UnixException.translateToIOException(UnixException.java:92)
        at java.base/sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:111)
        at java.base/sun.nio.fs.UnixException.rethrowAsIOException(UnixException.java:116)
        at java.base/sun.nio.fs.UnixFileAttributeViews$Basic.readAttributes(UnixFileAttributeViews.java:55)
        at java.base/sun.nio.fs.UnixFileSystemProvider.readAttributes(UnixFileSystemProvider.java:145)
        at java.base/sun.nio.fs.LinuxFileSystemProvider.readAttributes(LinuxFileSystemProvider.java:99)
        at java.base/java.nio.file.Files.readAttributes(Files.java:1763)
        at java.base/java.util.zip.ZipFile$Source.get(ZipFile.java:1222)
        at java.base/java.util.zip.ZipFile$CleanableResource.<init>(ZipFile.java:824)
        at java.base/java.util.zip.ZipFile$CleanableResource$FinalizableResource.<init>(ZipFile.java:850)
        at java.base/java.util.zip.ZipFile$CleanableResource.get(ZipFile.java:839)
        at java.base/java.util.zip.ZipFile.<init>(ZipFile.java:246)
        at java.base/java.util.zip.ZipFile.<init>(ZipFile.java:176)
        at java.base/java.util.jar.JarFile.<init>(JarFile.java:346)
        at java.base/sun.net.www.protocol.jar.URLJarFile.<init>(URLJarFile.java:103)
        at java.base/sun.net.www.protocol.jar.URLJarFile.getJarFile(URLJarFile.java:72)
        at java.base/sun.net.www.protocol.jar.JarFileFactory.get(JarFileFactory.java:99)
        at java.base/sun.net.www.protocol.jar.JarURLConnection.connect(JarURLConnection.java:125)
        at java.base/sun.net.www.protocol.jar.JarURLConnection.getInputStream(JarURLConnection.java:155)
        at org.apache.hadoop.conf.Configuration.parse(Configuration.java:2986)
        at org.apache.hadoop.conf.Configuration.getStreamReader(Configuration.java:3082)
        at org.apache.hadoop.conf.Configuration.loadResource(Configuration.java:3040)
        ... 10 more
```