# Purpose

Demonstrates the usage of Quartz and behavior in case we run in multiple nodes.

# Test Setup
## Configuration
- JDBC Job Store
- One Thread in the Executor
- Clustered
## Requirements
- Assumes PostgreSQL DB runs on localhost:5432 with postgres / postgres
- Assumes Quartz Tables are installed -- see also JdbcQuartzJobTest how to setup

# How to run

1. Build the code
```mvn clean install -DskipTests=true```
2. Start in one window just node (index 2)
```java -jar ./target/jobs-0.0.1-SNAPSHOT.jar 2 0 true```
3. Start in a second window a second node (index 1) and trigger 20 jobs
```java -jar ./target/jobs-0.0.1-SNAPSHOT.jar 2 0 true```

![Output produced](https://github.com/sterlp/training/blob/master/jobs/quartz_two_node_output.png)

# Arguments

1. Index of the node -- *number*
2. Count of jobs to trigger -- *number*
3. If a worker should be registered or not -- *boolean* as it is in a cluster only one nodes has to do so

# Links
* http://www.quartz-scheduler.org/documentation/quartz-2.x/configuration/ConfigJDBCJobStoreClustering.html
* https://www.ebayinc.com/stories/blogs/tech/performance-tuning-on-quartz-scheduler/
* http://airboxlab.github.io/performance/scalability/scheduler/quartz/2017/06/20/perf_tuning_quartz.html
* https://github.com/Flipkart/quartz/tree/master/distribution/examples/src/main/java/org/quartz/examples
