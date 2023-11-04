# **AWS Elastic MapReduce (EMR) Cheat Sheet**

- **What is EMR?**
  - Managed Hadoop framework.
  - Runs on EC2 instances.
  - More than just Hadoop: includes Spark, Hbase, Presto, Flink, Hive, etc.

- **Key Components:**
  - **EMR Notebook:** Similar to Jupyter Notebook; integrated with AWS services.
  - **Cluster:** Collection of EC2 instances (nodes).
    - **Master node (Leader node):** Manages the cluster, coordinates data and tasks distribution.
    - **Core nodes:** Run tasks, store data in HDFS.
    - **Task nodes:** Only run tasks, do not store data (suitable for spot instances).

- **Node Types:**
  - **Master Node:** Manages and monitors the cluster.
  - **Core Node:** Stores data in HDFS and runs tasks.
  - **Task Node:** Computes without HDFS interaction (ephemeral).

- **Cluster Types:**
  - **Transient Cluster:** Automatically terminates after predefined tasks are completed.
  - **Long-Running Cluster:** Manually terminated; suitable for ad hoc queries and exploratory data work.

- **Storage Options:**
  - **HDFS (Hadoop Distributed File System):** Default; distributed across instances.
  - **EMRFS (Amazon S3):** Use S3 as an HDFS, with optional S3 consistency via DynamoDB.
  - **Local File System:** Ephemeral, not distributed.
  - **EBS (Elastic Block Storage):** Optional for backing HDFS.

- **Integration Points:**
  - **Amazon VPC:** Virtual network for clusters.
  - **Amazon S3:** For input/output data storage.
  - **Amazon CloudWatch:** Monitoring and alarms.
  - **IAM:** Permissions management.
  - **AWS CloudTrail:** Audit trails for service requests.
  - **AWS Data Pipeline:** Scheduling and starting predefined clusters.

- **Other Features:**
  - **Resizing:** Core and Task nodes can be resized; Task nodes can be added/removed on the fly.
  - **Spot Instances:** Cost-effective for Task nodes.
  - **Charges:** Hourly rate + EC2 charges.
  - **Auto Scaling:** Automatic node provisioning if a Core node fails.

Based on the provided transcript about Amazon EMR (Elastic MapReduce), here are some practice exam questions along with answers and explanations:

## Practice Exam Questions:

**Question 1**: What is the role of the Master node in an EMR cluster?
A. To store data on the Hadoop Distributed File System (HDFS)
B. To run tasks and process data only
C. To manage the cluster and coordinate the distribution of tasks
D. To store permanent files for computation purposes only

**Question 2**: Which of the following are core components that come pre-installed with EMR? (Select TWO)
A. Oracle Database
B. Spark
C. HBase
D. MySQL
E. MongoDB

**Question 3**: True or False: Task nodes in an EMR cluster store data on the Hadoop Distributed File System (HDFS).

**Question 4**: What is a key advantage of using Amazon S3 with EMRFS instead of HDFS?
A. S3 provides a consistent view using DynamoDB for consistency tracking.
B. S3 is a relational database service optimized for EMR.
C. S3 storage is ephemeral and goes away after the cluster is terminated.
D. S3 allows the use of EC2 instances as storage nodes.

**Question 5**: Which type of EMR cluster should be used when you have a repeatable sequence of tasks and want to terminate the cluster automatically after these tasks are completed?
A. Long-Running cluster
B. Single-Node cluster
C. Transient cluster
D. Reserved cluster

## Answers and Explanations

**Answer 1**: C. To manage the cluster and coordinate the distribution of tasks

**Explanation**: The Master node in an EMR cluster is responsible for managing the cluster. It coordinates the distribution of tasks and data among other nodes for processing, tracks the status of tasks, and monitors the health of the cluster.

**Answer 2**: B. Spark and C. HBase

**Explanation**: Spark, HBase, Presto, Flink, and Hive are mentioned as technologies that come preinstalled with EMR, expanding its functionality beyond just Hadoop and MapReduce.

**Answer 3**: False

**Explanation**: Task nodes do not store data on HDFS. They are used only for computation purposes, which allows them to be good candidates for spot instances. They can be added to or removed from the cluster as needed without impacting the cluster's storage.

**Answer 4**: A. S3 provides a consistent view using DynamoDB for consistency tracking.

**Explanation**: Using S3 with EMRFS is advantageous because it can be used in place of HDFS while still providing high performance. EMRFS even offers an optional Consistent View feature for S3 consistency, which can use DynamoDB to track consistency.

**Answer 5**: C. Transient cluster

**Explanation**: A Transient cluster in EMR is configured to terminate automatically once all the predefined steps to run on it have been completed, making it cost-effective for repeatable tasks that do not require the cluster to be running continuously.
