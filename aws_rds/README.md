# AWS RDS: A Beginner's Guide

## Table of Contents

1. **Overview of Databases**
    - What is a Database?
    - Types of Databases: Relational (SQL) and Non-Relational (NoSQL)
    - Understanding SQL and NoSQL
    - Primary Keys and Composite Keys

2. **Databases on EC2 Instances**
    - Managing Databases on EC2
    - Challenges and Limitations

3. **Overview of Amazon RDS**
    - What is Amazon RDS?
    - Benefits of Amazon RDS
    - Supported Database Engines

4. **Migrating Traditional Databases from EC2 to RDS**
    - Steps to Migrate Databases
    - Best Practices for Migration

5. **High Availability (HA) - Multi-AZ Architecture**
    - Ensuring High Availability with Multi-AZ Setup
    - Failover and its Importance

6. **RDS - Multi-AZ Architecture**
    - Configuring Multi-AZ Deployments
    - Benefits and Use Cases

7. **RDS - Automatic Backup, Snapshots, and Restore**
    - Understanding Automatic Backups
    - Creating Manual Snapshots
    - Database Restoration Process

8. **RDS - Read Replicas**
    - Implementing Read Replicas for Scalability
    - Load Balancing and Read-Only Instances

9. **RDS - Data Security**
    - Security Best Practices
    - Encryption Options
    - IAM Authentication and Authorization

---

## 1. Overview of Databases

### What is a Database?
A **database** is a system that stores and manages data. There are two main types: **Relational (SQL)** and **Non-Relational (NoSQL)** databases.

### Types of Databases: Relational SQL and Non-Relational NoSQL
**Relational SQL Databases** use structured query language and define relationships between tables through schemas. Every table has a **primary key**, ensuring unique identification for each record.

**NoSQL Databases**, on the other hand, encompass diverse data models and don't adhere to a fixed schema. They are ideal for unstructured or semi-structured data.

### Primary Keys and Composite Keys
A **primary key** is a unique identifier for a record in a table. In SQL, every row and column must have a value, and the primary key ensures this uniqueness. A **composite key** is formed when a table's primary key includes multiple columns, linking it to another table.

---

## 2. Databases on EC2 Instances

### Managing Databases on EC2
Databases can be deployed on **EC2 instances**, providing flexibility and customization options.

### Challenges and Limitations
- **Scalability:** Limited scalability for large datasets.
- **High Availability:** Ensuring continuous availability is complex.

---

## 3. Overview of Amazon RDS

### What is Amazon RDS?
**Amazon RDS (Relational Database Service)** is a managed database service that simplifies database setup, operation, and scaling.

### Benefits of Amazon RDS
- **Automated Backups:** RDS automates backup tasks.
- **High Availability:** Multi-AZ deployments ensure failover support.
- **Scalability:** Read replicas provide scalable read operations.
- **Security:** Built-in security features for data protection.

### Supported Database Engines
RDS supports various database engines, including MySQL, PostgreSQL, SQL Server, and Oracle.

---

## 4. Migrating Traditional Databases from EC2 to RDS

### Steps to Migrate Databases
1. **Assessment:** Evaluate existing database structure and dependencies.
2. **Schema Conversion:** Modify schema for compatibility if needed.
3. **Data Migration:** Migrate data to RDS using tools like AWS Database Migration Service.
4. **Testing:** Validate data integrity and application compatibility.
5. **Switch Over:** Update application configurations to use RDS endpoint.

### Best Practices for Migration
- **Plan Carefully:** Thoroughly plan the migration process.
- **Backup Data:** Create backups before migration for safety.
- **Monitor Performance:** Monitor RDS performance post-migration.

---

## 5. High Availability (HA) - Multi-AZ Architecture

### Ensuring High Availability with Multi-AZ Setup
**Multi-AZ deployments** replicate data across multiple Availability Zones to ensure high availability and failover support.

### Failover and its Importance
**Failover** automatically switches to a standby replica in case of primary database failure, minimizing downtime and ensuring business continuity.

---

## 6. RDS - Multi-AZ Architecture

### Configuring Multi-AZ Deployments
1. **Enable Multi-AZ:** Enable Multi-AZ during RDS instance creation or modification.
2. **Automatic Failover:** RDS handles failover seamlessly.
3. **Read Replicas:** Multi-AZ setups can also utilize read replicas for read scalability.

### Benefits and Use Cases
- **Enhanced Reliability:** Multi-AZ ensures reliability and data redundancy.
- **Disaster Recovery:** Protects against data center failures.
- **Scaling:** Supports read scalability via read replicas.

---

## 7. RDS - Automatic Backup, Snapshots, and Restore

### Understanding Automatic Backups
RDS automatically takes daily backups of your database, allowing point-in-time recovery within a retention period.

### Creating Manual Snapshots
**Manual snapshots** provide additional backup points and are user-initiated.

### Database Restoration Process
1. **Select Snapshot:** Choose the snapshot to restore from.
2. **Configure Options:** Configure instance settings and security options.
3. **Restore:** Confirm the restoration process, and RDS handles the rest.

---

## 8. RDS - Read Replicas

### Implementing Read Replicas for Scalability
- **Create Read Replica:** Replicate data from the primary RDS instance.
- **Load Balancing:** Distribute read traffic across multiple read replicas.
- **Scaling Reads:** Improves read performance for applications with heavy read operations.

### Load Balancing and Read-Only Instances
Load balancers distribute traffic among multiple read replicas, optimizing performance. Read-only instances ensure data consistency and integrity.

---

## 9. RDS - Data Security

### Security Best Practices
- **Network Security:** Use Virtual Private Cloud (VPC) and security groups.
- **Encryption:** Encrypt data at rest and in transit for enhanced security.
- **IAM Authentication:** Implement IAM-based authentication and authorization.
- **Regular Updates:** Keep database engine and RDS instances updated for security patches.


# RDS - Kind of Database Server as a Service

## Managed Database Instances

Amazon RDS provides a managed database service for one or more databases, supporting various database engines, including:

- **MySQL**
- **MariaDB**
- **PostgreSQL**
- **Oracle**
- **Microsoft SQL**

**Amazon Aurora**, although related to RDS, is a distinct product with unique features and capabilities.

### Understanding CNAME (Canonical Name)

Databases connect through a **CNAME (Canonical Name)**, enabling straightforward communication. RDS utilizes standard database engines for seamless integration and compatibility.

### Database Optimization and Instance Provisioning

When provisioning an instance, you choose storage and instance types optimized for specific use cases:

- **bd.m5 general:** Balanced compute and memory for general applications.
- **db.r5 memory:** High memory instances for memory-intensive workloads.
- **db.t3 burst:** Burstable instances for workloads with variable CPU usage.

### Dedicated Storage Provisioning

Provisioned storage is dedicated to the instance and utilizes **EBS (Elastic Block Store)**, residing in the same Availability Zone (AZ) as the instance. However, this means RDS is susceptible to AZ-specific failures.

### Storage Options: SSD vs. Magnetic

You can choose between **SSD (Solid State Drive)** and **magnetic storage** options based on performance and cost requirements. SSD offers higher performance, while magnetic storage is more economical.

### Billing and Cost Structure

Billing for RDS operates on a per-instance basis with an hourly rate for compute resources. You are also billed for the allocated storage. It's crucial to consider both instance type and storage needs while estimating costs.

# RDS Demo: Creating a MariaDB Database Instance on AWS RDS

## Step 1: Navigate to AWS RDS Console

1. Go to the **AWS RDS Dashboard**.

## Step 2: Create a Subnet Group

1. Click on **Subnet Groups** in RDS.
2. Create a new DB Subnet Group named **demo-rds**.
3. Choose your VPC.
4. Add subnets and Availability Zones (AZs) to the group.

## Step 3: Create a Database Instance

1. Click on **Create Database**.
2. Choose **Standard Create** and select **MariaDB**.
3. Choose the database version or use the latest version.
4. Select a template (e.g., production or dev/test).

## Step 4: Configuration Settings

### Basic Settings:

- **Database Identifier:** Provide a unique name for your database.
- **Master Username:** Specify the username and password for the master user.
- **Database Instance Class:** Choose the instance class (e.g., db.t2.micro).
- **Storage Type:** Select SSD GP2 with a storage size of 20GB.
- **Auto Scaling:** Optionally enable auto scaling (not recommended for testing).

### Connectivity:

- **Network Type:** Choose IPv4.
- **VPC:** Select your desired VPC.
- **Subnet Group:** Pick the subnet group you created.
- **VPC Security Group:** Select an existing security group for your database instance.
- **Database Authentication:** Choose the authentication method as per your requirement.

### Additional Configuration:

- **Initial Database:** Specify the name of the initial database to be created.
- **Backups:** Set the retention period for automated backups.
- **Copy Tags to Snapshots:** Enable if needed.
- **Maintenance and Monitoring:** Configure maintenance window and enable enhanced monitoring if desired.

## Step 5: Create Database

1. Review your configuration settings.
2. Click on **Create Database**.

AWS RDS will now create your MariaDB database instance based on the provided configuration. Once the instance is created, you can connect to it using the provided endpoint and begin using your managed database on Amazon RDS.

## Details: Connectivity & Security

### Endpoint:

The **Endpoint** is a unique and unchanging address used to access your RDS database. It's crucial for connecting applications to your database securely and reliably.

### Migrating a Database from EC2 to RDS

1. **Get the Dump of Your Existing DB on EC2:**
   ```bash
   mysqldump -u root -p ec2db > ec2db.sql
   ```

2. **Connect to Your RDS DB Instance:**
   ```bash
   mysql -h <providerdsendpoint> -P 3306 -u rdsuser -p rdsdb < ec2db.sql
   ```
   Replace `<providerdsendpoint>`, `rdsuser`, and `rdsdb` with your RDS instance endpoint, username, and database name respectively. The `-p` flag prompts for the password.

   Note: `-p rdsdb` specifies the name used when creating the initial database on RDS.

3. **Verifying Data:**
   You can verify the data to ensure successful migration.

## RDS Multi-AZ Setup

In **Multi-AZ setup**, secondary hardware is provisioned in another Availability Zone, ensuring high availability and failover support. However, there are specific considerations:

- **Access via Database CNAME:**
  Access to RDS is allowed only via the database **CNAME (Canonical Name)**. The CNAME points to the primary instance. Standby replicas cannot be accessed directly for any purpose.

- **Usage Limitations of Standby Replica:**
  Standby replicas in Multi-AZ setup cannot be used to enhance capacity. They serve as failover targets and ensure data redundancy.

- **Synchronous Replication:**
  RDS utilizes synchronous replication to maintain consistency across primary and standby instances, ensuring data integrity in case of failover.

## RDS Backups and Restores: Understanding RPO, RTO, and Backup Mechanisms

### **RPO (Recovery Point Objective) and RTO (Recovery Time Objective)**

- **RPO (Recovery Point Objective):**
  - RPO represents the time between the last backup and when a failure occurred.
  - It defines the maximum acceptable data loss in case of a failure.
  - Businesses typically provide an RPO value, which influences technical solutions and costs.

- **RTO (Recovery Time Objective):**
  - RTO is the time between a disaster recovery event and full recovery.
  - It is influenced by processes, staff availability, technology, and documentation.

### **RDS Backups**

- **First Snapshot:**
  - The first snapshot captures the full size of consumed data.
  - Manual snapshots persist in your AWS account even after their lifecycle and require manual deletion.

- **Backup Mechanism:**
  - Automatic backups use incremental backup technology.
  - Every 5 minutes, transaction logs are saved to S3, enabling restoration to any 5-minute point in time.
  - Automatic cleanup can be configured from 0 to 35 days.
  - When a database is deleted, backups can be retained based on the retention period.

- **Database Logs:**
  - Database logs can be stored in S3, providing additional data recovery options.

### **Points to Remember during Restores:**

- **Creating New RDS Instance:**
  - During restoration, RDS creates a new instance with a new endpoint address.

- **Manual vs. Automated Backups:**
  - Restoring a manual snapshot sets the database to a specific point in time, influencing RPO.
  - Automated backups enable restoration to any 5-minute point in time using transaction logs.

- **Replaying Transaction Logs:**
  - Backups are restored, and transaction logs are replayed to bring the database to the desired point in time.
  - Restores may not be fast; consider RTO while planning.

### **RDS Read-Replicas**

- **Asynchronous Nature:**
  - Read replicas operate asynchronously with the primary instance.
  - Data is fully written to the primary instance before being pushed to read replicas.

- **Scaling Read Operations:**
  - Each DB instance supports up to 5 direct read replicas.
  - Read replicas provide additional instances for read performance, allowing scaling out read operations.

- **Chaining and Lag:**
  - Read replicas can be chained, but lag can become a problem, impacting data consistency.

- **Global Performance Improvements:**
  - Cross-region replicas can be used to achieve global performance improvements, extending read capabilities across different AWS regions.