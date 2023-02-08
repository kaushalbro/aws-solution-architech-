# Exam SAA-C03

- [Design Secure Architectures](#Design-Secure-Architectures)
- [Design Resilient Architectures](#Design-Resilient-Architectures)
- [Design High-Performing Architectures](#Design-High-Performing-Architectures)
- [Design Cost-Optimized Architectures](#Design-Cost-Optimized-Architectures)
- [Appendix](#Appendix)
- [Practise Questions](#Practise-Questions)

## Design Secure Architectures

### Task Statement 1: Design secure access to AWS resources.

#### Knowledge of:

1. Access controls and management across multiple accounts.

    * AWS organizations is an account management service that enables you to consolidate multiple AWS accounts into an organization that you create and centrally manage.

    * Always enable multi-factor authentication on the root account. Always use a strong and complex password on the root account. The paying account should be used for billing purposes only. Do not deploy resources into the paying account. Enable/Disable AWS services using Service Control Policies (SCP) either on the OU or on individual accounts.

1. AWS federated access and identity services (for example, AWS Identity and Access Management [IAM], AWS Single Sign-On [AWS SSO]).

    * AWS IAM Identity Center makes it easy to centrally manage federated access to multiple AWS accounts and business applications and provide users with single sign-on access to all their assigned accounts and applications from one place.

    * AWS IAM Identity Center works with an IdP of your choice, such as Okta Universal Directory or Azure Active Directory (AD) via the Security Assertion Markup Language 2.0 (SAML 2.0) protocol.

1. AWS global infrastructure (for example, Availability Zones, AWS Regions).

    * A Region is a location. An Availability Zone is a Data Center. An Availability Zone may contain several Data Centres that are close to each other (within 100 km).

    * Edge locations are endpoints for AWS that are used for caching content. There are many more edge locations than regions.

1. AWS security best practices (for example, the principle of least privilege).

    * Only assign a user the minimum number of privileges they need to do their job.

1. The AWS shared responsibility model.

    * AWS are responsible for security of the Cloud. The customer is responsible for the security in the Cloud. If you can do it in the AWS Management Console you are generally responsible for it. Encryption is a shared responsibility.

#### Skills in:

1. Applying AWS security best practices to IAM users and root users (for example, multi-factor authentication [MFA]).

1. Designing a flexible authorization model that includes IAM users, groups, roles, and policies.

    * Permissions are assigned using IAM policy documents (consisting of JSON). A user is a physical person, a group is a function such as administrator and contains users, and roles are used internally within AWS to allow access from one service to another. A permission should be assigned to a group and then users inherit the permissions of the groups they are assigned. An explicit deny will always overwrite an allow.

1. Designing a role-based access control strategy (for example, AWS Security Token Service [AWS STS], role switching, cross-account access).

    * Cross-account role access gives you the ability to set up temporary access you can easily control.

1. Designing a security strategy for multiple AWS accounts (for example, AWS Control Tower, service control policies [SCPs]).

    * SCPs are the only way to restrict what the root account can do.

1. Determining the appropriate use of resource policies for AWS services.

1. Determining when to federate a directory service with IAM roles.

### Task Statement 2: Design secure workloads and applications.

#### Knowledge of:

1. Application configuration and credentials security.

1. AWS service endpoints.

1. Control ports, protocols, and network traffic on AWS.

1. Secure application access.

1. Security services with appropriate use cases (for example, Amazon Cognito, Amazon GuardDuty, Amazon Macie).

1. Threat vectors external to AWS (for example, DDoS, SQL injection).

    * Common DDoS attacks include layer 4 attacks such as SYN floods or NTP amplification attacks. Common Layer 7 attacks include floods of GET/POST requests.

#### Skills in:

1. Designing VPC architectures with security components (for example, security groups, route tables, network ACLs, NAT gateways).

    * A standard architecture is shown below:
        <p align="center">
            <img src="/res/VPC_architecture.JPG">
        </p>

1. Determining network segmentation strategies (for example, using public subnets and private subnets).

1. Integrating AWS services to secure applications (for example, AWS Shield, AWS WAF, AWS SSO, AWS Secrets Manager).

1. Securing external network connections to and from the AWS Cloud (for example, VPN, AWS Direct Connect).

### Task Statement 3: Determine appropriate data security controls.

#### Knowledge of:

1. Data access and governance.

1. Data recovery.

1. Data retention and classification.

1. Encryption and appropriate key management.

#### Skills in:

1. Aligning AWS technologies to meet compliance requirements.

1. Encrypting data at rest (for example, AWS Key Management Service [AWS KMS]).

1. Encrypting data in transit (for example, AWS Certificate Manager [ACM] using TLS).

1. Implementing access policies for encryption keys.

1. Implementing data backups and replications.

1. Implementing policies for data access, lifecycle, and protection.

1. Rotating encryption keys and renewing certificates.

## Design Resilient Architectures

### Task Statement 1: Design scalable and loosely coupled architectures

#### Knowledge of:

1. API creation and management (for example, Amazon API Gateway, REST API).

1. AWS managed services with appropriate use cases (for example, AWS Transfer Family, Amazon Simple Queue Service [Amazon SQS], Secrets Manager).

    * The AWS Transfer Family allows you to easily move files in and out of S3 or EFS using SFTP, FTPS, or FTP. It excels with bringing legacy application storage to the cloud.

1. Caching strategies.

1. Design principles for microservices (for example, stateless workloads compared with stateful workloads).

1. Event-driven architectures.

1. Horizontal scaling and vertical scaling.

    * Always spread out over multiple AZs.

    * Auto-scaling is only for EC2. Other services might have a scaling option, but they aren't included in auto-scaling groups.

    * Ideally you should get ahead of the workload. Favour solutions that are predictive rather than reactive.

    * AMIs should be baked to reduce build times. Reduce the amount of work required in User Data scripts to increase provisioning times.

    * Steady state groups allow us to create a situation where the failure of a legacy codebase or resource that can't be scaled can automatically recover from failure.

    * ELBs are essential. Make sure you enable health checks from load balancers. This will allow instances to be terminated and replaced when they fail health checks.

    * RDS has the most database scaling options. Horizontal scaling is usually preferred over vertical. Read replicas are your friend. DynamoDB scaling comes down to access patterns.

1. How to appropriately use edge accelerators (for example, content delivery network [CDN]).

1. How to migrate applications into containers.

1. Load balancing concepts (for example, Application Load Balancer).

1. Multi-tier architectures.

1. Queuing and messaging concepts (for example, publish/subscribe).

1. Serverless technologies and patterns (for example, AWS Fargate, AWS Lambda).

1. Storage types with associated characteristics (for example, object, file, block).

1. The orchestration of containers (for example, Amazon Elastic Container Service [Amazon ECS], Amazon Elastic Kubernetes Service [Amazon EKS]).

1. When to use read replicas.

    * RDS Read replicas are for scaling read performance and not for disaster recovery. Key facts include:
        * A read replica can be cross-AZ and cross-region.
        * Each read replica has its own DNS endpoint.
        * Read replicas require automatic backup to be enabled.
        * Read replicas can be promoted to be their own database. This breaks the replication.

1. Workflow orchestration (for example, AWS Step Functions).

    * Loose coupling is strongly preferred over tight coupling.

#### Skills in:

1. Designing event-driven, microservice, and/or multi-tier architectures based on requirements.

1. Determining scaling strategies for components used in an architecture design.

1. Determining the AWS services required to achieve loose coupling based on requirements.

1. Determining when to use containers.

    * Containers are generally seen as more flexible. They're easier to run on-site and move around to different environments.

1. Determining when to use serverless technologies and patterns.

    * Serverless allows you to focus on the application and only when it is necessary. The below diagram is useful:
        <p align="center">
        <img src="/res/serverless.JPG">
        </p>

1. Recommending appropriate compute, storage, networking, and database technologies based on requirements.

1. Using purpose-built AWS services for workloads.

### Task Statement 2: Design highly available and/or fault-tolerant architectures.

#### Knowledge of:

1. AWS global infrastructure (for example, Availability Zones, AWS Regions, Amazon Route 53).

    * A Region is a physical location in the world which consists of two or more Availability Zones (AZ's).

    * An AZ is one or more discrete data centres, each with redundant power, networking, and connectivity, housed in separate facilities.

    * Edge Locations are endpoints for AWS which are used for caching content. Typically, this consists of CloudFront, Amazon's Content Delivery Network (CDN).

1. AWS managed services with appropriate use cases (for example, Amazon Comprehend,
Amazon Polly).

1. Basic networking concepts (for example, route tables).

1. Disaster recovery (DR) strategies (for example, backup and restore, pilot light, warm standby, active-active failover, recovery point objective [RPO], recovery time objective [RTO]).

1. Distributed design patterns.

1. Failover strategies.

1. Immutable infrastructure.

1. Load balancing concepts (for example, Application Load Balancer).

1. Proxy concepts (for example, Amazon RDS Proxy).

1. Service quotas and throttling (for example, how to configure the service quotas for a workload in a standby environment).

1. Storage options and characteristics (for example, durability, replication).

1. Workload visibility (for example, AWS X-Ray).

#### Skills in:

1. Determining automation strategies to ensure infrastructure integrity.

1. Determining the AWS services required to provide a highly available and/or fault-tolerant architecture across AWS Regions or Availability Zones.

1. Identifying metrics based on business requirements to deliver a highly available solution.

1. Implementing designs to mitigate single points of failure.

1. Implementing strategies to ensure the durability and availability of data (for example, backups).

1. Selecting an appropriate DR strategy to meet business requirements.

1. Using AWS services that improve the reliability of legacy applications and applications not built for the cloud (for example, when application changes are not possible).

1. Using purpose-built AWS services for workloads.

## Design High-Performing Architectures

### Task Statement 1: Determine high-performing and/or scalable storage solutions.

#### Knowledge of:

1. Hybrid storage solutions to meet business requirements.

1. Storage services with appropriate use cases (for example, Amazon S3, Amazon Elastic File System [Amazon EFS], Amazon Elastic Block Store [Amazon EBS]).

1. Storage types with associated characteristics (for example, object, file, block).

#### Skills in:

1. Determining storage services and configurations that meet performance demands.

1. Determining storage services that can scale to accommodate future needs.

### Task Statement 2: Design high-performing and elastic compute solutions.

#### Knowledge of:

1. AWS compute services with appropriate use cases (for example, AWS Batch, Amazon EMR, Fargate).

1. Distributed computing concepts supported by AWS global infrastructure and edge services.

1. Queuing and messaging concepts (for example, publish/subscribe).

1. Scalability capabilities with appropriate use cases (for example, Amazon EC2 Auto Scaling, AWS Auto Scaling).

1. Serverless technologies and patterns (for example, Lambda, Fargate).

1. The orchestration of containers (for example, Amazon ECS, Amazon EKS).

#### Skills in:

1. Decoupling workloads so that components can scale independently.

1. Identifying metrics and conditions to perform scaling actions.

1. Selecting the appropriate compute options and features (for example, EC2 instance types) to meet business requirements.

1. Selecting the appropriate resource type and size (for example, the amount of Lambda memory) to meet business requirements.

### Task Statement 3: Determine high-performing database solutions.

#### Knowledge of:

1. AWS global infrastructure (for example, Availability Zones, AWS Regions).

1. Caching strategies and services (for example, Amazon ElastiCache).

1. Data access patterns (for example, read-intensive compared with write-intensive).

1. Database capacity planning (for example, capacity units, instance types, Provisioned IOPS).

1. Database connections and proxies.

1. Database engines with appropriate use cases (for example, heterogeneous migrations, homogeneous migrations).

    * ACID stands for Atomic, Consistent, Isolated, and Durable:
        * **Atomic:** All changes to data must be performed successfully or not at all.
        * **Consistent:** Data must be in a consistent state before and after the transaction.
        * **Isolated:** No other process can change the data while the transaction is running.
        * **Durable:** The changes made by a transaction must persist. 

1. Database replication (for example, read replicas).

1. Database types and services (for example, serverless, relational compared with non-relational, in-memory).

#### Skills in:

1. Configuring read replicas to meet business requirements.

1. Designing database architectures.

1. Determining an appropriate database engine (for example, MySQL compared with
PostgreSQL).

1. Determining an appropriate database type (for example, Amazon Aurora, Amazon DynamoDB).

1. Integrating caching to meet business requirements.

### Task Statement 4: Determine high-performing and/or scalable network architectures.

#### Knowledge of:

1. Edge networking services with appropriate use cases (for example, Amazon CloudFront, AWS Global Accelerator).

1. How to design network architecture (for example, subnet tiers, routing, IP addressing).

1. Load balancing concepts (for example, Application Load Balancer).

1. Network connection options (for example, AWS VPN, Direct Connect, AWS PrivateLink).

#### Skills in:

1. Creating a network topology for various architectures (for example, global, hybrid, multi-tier).

1. Determining network configurations that can scale to accommodate future needs.

1. Determining the appropriate placement of resources to meet business requirements.

1. Selecting the appropriate load balancing strategy.

### Task Statement 5: Determine high-performing data ingestion and transformation solutions.

#### Knowledge of:

1. Data analytics and visualization services with appropriate use cases (for example, Amazon Athena, AWS Lake Formation, Amazon QuickSight).

1. Data ingestion patterns (for example, frequency).

1. Data transfer services with appropriate use cases (for example, AWS DataSync, AWS Storage Gateway).

    * AWS DataSync is used to move large amounts of data from on-premises to AWS. It is used with NFS and SMB compatible file systems. The replication can be done hourly, daily, or weekly. The DataSync agent is required to start the replication. It can be used to replicate EFS to EFS.

    * AWS DataSync automatically encrypts data and accelerates transfer over the WAN. DataSync performs automatic data integrity checks in-transit and at-rest.

    * AWS DataSync is best for a one-time migration, and a hybrid architecture with continuous sync is more suited for Storage Gateway.

1. Data transformation services with appropriate use cases (for example, AWS Glue).

1. Secure access to ingestion access points.

1. Sizes and speeds needed to meet business requirements.

1. Streaming data services with appropriate use cases (for example, Amazon Kinesis).

#### Skills in:

1. Building and securing data lakes.

1. Designing data streaming architectures.

1. Designing data transfer solutions.

1. Implementing visualization strategies.

1. Selecting appropriate compute options for data processing (for example, Amazon EMR).

1. Selecting appropriate configurations for ingestion.

1. Transforming data between formats (for example, .csv to .parquet).

## Design Cost-Optimized Architectures

### Task Statement 1: Design cost-optimized storage solutions.

#### Knowledge of:

1. Access options (for example, an S3 bucket with Requester Pays object storage).

1. AWS cost management service features (for example, cost allocation tags, multi-account billing).

1. AWS cost management tools with appropriate use cases (for example, AWS Cost Explorer, AWS Budgets, AWS Cost and Usage Report).

1. AWS storage services with appropriate use cases (for example, Amazon FSx, Amazon EFS, Amazon S3, Amazon EBS).

1. Backup strategies.

1. Block storage options (for example, hard disk drive [HDD] volume types, solid state drive [SSD] volume types).

1. Data lifecycles.

1. Hybrid storage options (for example, DataSync, Transfer Family, Storage Gateway).

1. Storage access patterns.

1. Storage tiering (for example, cold tiering for object storage).

1. Storage types with associated characteristics (for example, object, file, block).

#### Skills in:

1. Designing appropriate storage strategies (for example, batch uploads to Amazon S3 compared with individual uploads).

1. Determining the correct storage size for a workload.

1. Determining the lowest cost method of transferring data for a workload to AWS storage.

1. Determining when storage auto scaling is required.

1. Managing S3 object lifecycles.

1. Selecting the appropriate backup and/or archival solution.

1. Selecting the appropriate service for data migration to storage services.

1. Selecting the appropriate storage tier.

1. Selecting the correct data lifecycle for storage.

1. Selecting the most cost-effective storage service for a workload.

    * S3 pricing for US East (N. Virginia) is shown below:
        <p align="center">
        <img src="/res/storage_pricing.JPG">
        </p>

### Task Statement 2: Design cost-optimized compute solutions.

#### Knowledge of:

1. AWS cost management service features (for example, cost allocation tags, multi-account billing).

1. AWS cost management tools with appropriate use cases (for example, Cost Explorer, AWS Budgets, AWS Cost and Usage Report).

1. AWS global infrastructure (for example, Availability Zones, AWS Regions)

1. AWS purchasing options (for example, Spot Instances, Reserved Instances, Savings Plans)

1. Distributed compute strategies (for example, edge processing)

1. Hybrid compute options (for example, AWS Outposts, AWS Snowball Edge)

    * Snowball is a petabyte-scale data transport solution that uses secure appliances to transfer large amounts of data into and out of AWS. Using Snowball addresses common challenges with large-scale data transfers including high network costs, long transfer times, and security concerns. Transferring data with Snowball is simple, fast, secure, and can be as little as one-fifth the cost of high-speed internet.

    * Snowball comes in either a 50 TB or 80 TB size. Security controls include 256-bit encryption, and an industry-standard Trusted Platform Module (TPM) designed to ensure both security and full chain-of-custody of your data. Once the data job has been processed and verified, AWS performs a software erasure of the Snowball appliance.

    * AWS Snowball Edge is a 100 TB data transfer device with on-board storage and compute capabilities. You can use it to move large amounts of data into and out of AWS, as a temporary storage tier for large local datasets, or to support local workloads in remote or offline locations. Snowball Edge can cluster together to form a local storage tier and process your data on-premises, helping ensure your applications continue to run even when they are not able to access the cloud.

    * AWS Snowmobile is an Exabyte-scale data transfer service used to move extremely large amounts of data to AWS. You can transfer up to 100 PB per Snowmobile, a 45-foot long ruggedised shipping container, pulled by a semi-trailer truck. Snowmobile makes it easy to move massive volumes of data to the cloud, including video libraries, image repositories, or even a complete data centre migration.

    * A summary of when to consider Snowball is shown below:
        <p align="center">
        <img src="/res/snowball_use_case.JPG">
        </p>

1. Instance types, families, and sizes (for example, memory optimized, compute optimized, virtualization)

1. Optimization of compute utilization (for example, containers, serverless computing,
microservices)

1. Scaling strategies (for example, auto scaling, hibernation)

#### Skills in:

1. Determining an appropriate load balancing strategy (for example, Application Load Balancer [Layer 7] compared with Network Load Balancer [Layer 4] compared with Gateway Load Balancer).

1. Determining appropriate scaling methods and strategies for elastic workloads (for example, horizontal compared with vertical, EC2 hibernation).

1. Determining cost-effective AWS compute services with appropriate use cases (for example, Lambda, Amazon EC2, Fargate).

1. Determining the required availability for different classes of workloads (for example, production workloads, non-production workloads).

1. Selecting the appropriate instance family for a workload.

1. Selecting the appropriate instance size for a workload.

### Task Statement 3: Design cost-optimized database solutions.

#### Knowledge of:

1. AWS cost management service features (for example, cost allocation tags, multi-account billing).

1. AWS cost management tools with appropriate use cases (for example, Cost Explorer, AWS Budgets, AWS Cost and Usage Report).

1. Caching strategies.

1. Data retention policies.

1. Database capacity planning (for example, capacity units).

1. Database connections and proxies.

1. Database engines with appropriate use cases (for example, heterogeneous migrations, homogeneous migrations).

1. Database replication (for example, read replicas).

1. Database types and services (for example, relational compared with non-relational, Aurora, DynamoDB).

#### Skills in:

1. Designing appropriate backup and retention policies (for example, snapshot frequency).

1. Determining an appropriate database engine (for example, MySQL compared with
PostgreSQL).

1. Determining cost-effective AWS database services with appropriate use cases (for example, DynamoDB compared with Amazon RDS, serverless).

1. Determining cost-effective AWS database types (for example, time series format, columnar format).

1. Migrating database schemas and data to different locations and/or different database engines.

### Task Statement 4: Design cost-optimized network architectures.

#### Knowledge of:

1. AWS cost management service features (for example, cost allocation tags, multi-account billing).

1. AWS cost management tools with appropriate use cases (for example, Cost Explorer, AWS Budgets, AWS Cost and Usage Report).

1. Load balancing concepts (for example, Application Load Balancer).

1. NAT gateways (for example, NAT instance costs compared with NAT gateway costs).

1. Network connectivity (for example, private lines, dedicated lines, VPNs).

1. Network routing, topology, and peering (for example, AWS Transit Gateway, VPC peering).

    * VPC Peering allows you to connect 1 VPC with another via a direct network route using private IP addresses.

    * Instances behave as if they were on the same private network.

    * You can peer VPCs with other AWS accounts as well as with other VPCs in the same account.

    * Peering is in a star configuration (i.e. 1 central VPC peer with 4 others). There is no transitive peering.

    * You can peer between regions.

1. Network services with appropriate use cases (for example, DNS).

#### Skills in:

1. Configuring appropriate NAT gateway types for a network (for example, a single shared NAT gateway compared with NAT gateways for each Availability Zone).

1. Configuring appropriate network connections (for example, Direct Connect compared with VPN compared with internet).

1. Configuring appropriate network routes to minimize network transfer costs (for example, Region to Region, Availability Zone to Availability Zone, private to public, Global Accelerator, VPC endpoints).

    * VPC Endpoints are used when you want to connect AWS services without leaving the Amazon internal network. Interface endpoints and gateway endpoints (S3 and DynamoDB).

1. Determining strategic needs for content delivery networks (CDNs) and edge caching.

1. Reviewing existing workloads for network optimizations.

1. Selecting an appropriate throttling strategy.
 
1. Selecting the appropriate bandwidth allocation for a network device (for example, a single VPN compared with multiple VPNs, Direct Connect speed).

## Appendix

### Key Technologies and Concepts

1. Compute.

1. Cost management.

1. Database.

1. Disaster recovery.

1. High performance.

1. Management and governance.

1. Microservices and component decoupling.

1. Migration and data transfer.

    * AWS Migration Hub gives you a single place to track the process of your application migration to AWS. It integrates with Server Migration Service (SMS) and Database Migration Service (DMS).

    * SMS can create an on-premises architecture into EMIs. DMS can run migrate or convert on-premises databases through AWS Schema Conversion Tool.

1. Networking, connectivity, and content delivery.

1. Resiliency.

1. Security.

1. Serverless and event-driven design principles.

1. Storage.

### AWS Services and Features

#### Analytics

1. Amazon Athena.

    * Amazon Athena is an interactive query service which enables you to analyse and query data located in S3 using standard SQL.

    * Athena is serverless and you pay per query. There is no need to setup complex Extract/Transform/Load (ETL) processes, and it works directly with data stored in S3.

    * Athena can be used to query log files stored in S3. It can also be used to generate business reports on data stored in S3.

1. AWS Data Exchange.

    * AWS Data Exchange is a service that makes it easy for AWS customers to find, subscribe to, and use third-party data in the AWS Cloud.

    * As a subscriber, you can find and subscribe to thousands of products from qualified data providers. Then, you can use the AWS Data Exchange console or APIs to create, view, manage, and access data sets for use across a variety of AWS analytics and machine learning services.

1. AWS Data Pipeline.

    * AWS Data Pipeline is a managed AWS service that helps you reliably process and move data between different AWS compute and storage services, as well as on-premises data sources, at specified intervals. It is used for ETL workflows that automate movement and transformation of data.

    * With AWS Data Pipeline, you can regularly access your data where it’s stored, transform and process it at scale, and efficiently transfer the results to AWS services such as Amazon S3, Amazon RDS, Amazon DynamoDB, and Amazon EMR.

1. Amazon EMR.

    * Elastic MapReduce (EMR) is AWS's ETL tool. It is a managed fleet of EC2 instances that run open-source tools.

    * You can use RIs and Spot Instances to reduce your costs. The architecture lives inside a VPC.

1. AWS Glue.

    * Glue is a serverless data integration service that makes it easy to discover, prepare, and combine data. It allows you to perform ETL workloads without managing underlying servers.

1. Amazon Kinesis.

    * Kinesis allows you to ingest, process, and analyse real-time streaming data.

    * Kinesis Data Streams provides real-time streaming for ingesting data, which takes some effort to setup, and does not automatically scale. Data Firehose is a data transfer tool to get information to S3, Redshift, Elasticsearch, or Splunk, in near real time (within 60 seconds).

    * Kinesis Data Streams can be used as a message broker if you need real time.

1. AWS Lake Formation.

    * AWS Lake Formation is a service that makes it easy to set up, secure, and manage your data lake. With Lake Formation you can discover, cleanse, transform, and ingest data into your data lake from various sources, define fine-grained permissions at database, table or column level and then share controlled access across analytic, machine learning and ETL services.

1. Amazon Managed Streaming for Apache Kafka (Amazon MSK).

    * Amazon MSK is a fully managed service that makes it easy for you to build and run applications that use Apache Kafka to process streaming data. Apache Kafka is an open-source platform for building real-time streaming data pipelines and applications. With Amazon MSK, you can use native Apache Kafka APIs to populate data lakes, stream changes to and from databases, and power machine learning and analytics applications.

1. Amazon OpenSearch Service (Amazon Elasticsearch Service).

    * Elasticsearch is a fully managed version of the open-source application Elasticsearch. It allows you to quickly search over your stored data and analyse the data you get back. It is commonly used as part of an Elasticsearch, Logstash, and Kibana (ELK) stack. ELK can be used as a 3rd party logging solution.

1. Amazon QuickSight.

    * QuickSight is a fully managed BI data visualisation service. It allows you to easily create dashboards and share them within your company.

1. Amazon Redshift.

    * Redshift is a fully managed, petabyte-scale (up to 16 PB) data warehouse service in the cloud. It is a very large relational database traditionally used in big data applications. It is great for BI applications. It cannot take the place of RDS.

    * Redshift only supports single-AZ deployments. Backups are kept for 1 day by default and can be raised up to 35 days.

#### Application Integration

1. Amazon AppFlow.

    * Amazon AppFlow is a fully managed integration service that enables you to securely transfer data between Software-as-a-Service (SaaS) applications like Salesforce, SAP, Zendesk, Slack, and ServiceNow, and AWS services like Amazon S3 and Amazon Redshift, in just a few clicks.

1. AWS AppSync.

    * AWS AppSync allows your applications to access exactly the data they need. Create a flexible API to securely access, manipulate, and combine data from multiple sources. Pay only for requests to your API and for real-time messages delivered to connected clients.

1. Amazon EventBridge (Amazon CloudWatch Events).

    * EventBridge is a serverless event bus. It allows you to pass events from a source to an endpoint. It is the glue that holds your serverless application together.

    * It can be used to trigger an action based on something that happened in AWS. It holds together a serverless application and Lambda functions. Any API call that happens in AWS can alert a Lambda function, or a variety of different endpoints, that something has happened.

1. Amazon MQ.

    * Amazon MQ is a managed message broker service for Apache ActiveMQ and RabbitMQ that makes it easy to set up, migrate and operate message brokers on AWS Cloud.

    * Preferred over SNS with SQS for new applications, and required for anything specific to JMS and some other protocols. Note that Amazon MQ restricts access to private networking.

1. Amazon Simple Notification Service (Amazon SNS).

    * SNS is a fully managed messaging service for both application-to-application (A2A) and application-to-person (A2P) communication.

    * SNS is a push-based messaging service. It will proactively deliver messages to the endpoints subscribed to it. This can be used to alert a system or a person.

    * SNS Settings:
        * **Subscribers:** Kinesis Data Firehose, SQS, Lambda, email, HTTP(S), SMS, platform application endpoint etc.
        * **Message Size:** Messages can be up to 256 KB of text in any format.
        * **DLQ Support:** Messages that fail to be delivered can be stored in an SQS SLQ. Only HTTP(S) are retried automatically.
        * **FIFO or Standard:** FIFO only supports SQS as a subscriber.
        * **Encryption:** Messages are encrypted at transit by default, but you can add at-rest (a KMS key is required).
        * **Access Policy:** A resource policy can be added to a topic, similar to S3.

1. Amazon Simple Queue Service (Amazon SQS).

    * SQS is a fully managed message queuing service that enables you to decouple and scale microservices, distributed systems, and serverless applications. SQS enables asynchronous processing of work.

    * SQS Settings:
        * **Delivery Delay:** Delay between message showing up in the queue and being sent.
        * **Message Size:** Messages can be up to 256 KB of text in any format.
        * **Encryption:** Messages are encrypted at transit by default, but you can add at-rest (a KMS key is required).
        * **Message Retention:** Default is 4 days, but can be set between 1 minute and 14 days.
        * **Long vs Short:** Long polling isn't the default, but it should be for most use-cases.
        * **Queue Depth:** This can be a trigger for autoscaling.
        * **Visibility Timeout:** The period of time during which SQS prevents other consumers from receiving and processing the message. SQS doesn't delete the message, it is up to consumers to delete the message from the queue after receiving and processing it. Default of 30s.

    * A Dead-Letter Queue (DLQ) can be used to store messages that fail processing on the SQS. The message will eventually be lost as the longest retention period is 14 days. A DLQ is just a standard queue with the DLQ option set.

    * A standard SQS offers "best effort" ordering, with potentially duplicate messages, and nearly unlimited transactions per second. A FIFO SQS provides guaranteed ordering, no message duplication, and 300 messages per second. A FIFO SQS is also more expensive.

1. AWS Step Functions.

    * AWS Step Functions is a serverless orchestration service that lets you integrate with AWS Lambda functions and other AWS services to build business-critical applications. Through Step Functions' graphical console, you see your application’s workflow as a series of event-driven steps.

#### AWS Cost Management

1. AWS Budgets.

    * Budgets allow organisations to easily plan and set expectations around cloud costs. You can easily track your ongoing spend and create alerts to let users know when they're close to exceeding their allotted spend.

1. AWS Cost and Usage Report.

    * The AWS Cost and Usage Reports (AWS CUR) contains the most comprehensive set of cost and usage data available. You can use Cost and Usage Reports to publish your AWS billing reports to an Amazon Simple Storage Service (Amazon S3) bucket that you own. You can receive reports that break down your costs by the hour, day, or month, by product or product resource, or by tags that you define yourself. AWS updates the report in your bucket once a day in comma-separated value (CSV) format. You can view the reports using spreadsheet software such as Microsoft Excel or Apache OpenOffice Calc, or access them from an application using the Amazon S3 API.

1. AWS Cost Explorer.

    * Cost Explorer is an easy-to-use tool that allows you to visualise your cloud costs. You can generate reports based on a variety of factors, including resource tags.

1. Savings Plans.

    * Savings Plans is a flexible pricing model offering lower prices compared to On-Demand pricing, in exchange for a specific usage commitment (measured in $/hour) for a one or three-year period. AWS offers three types of Savings Plans – Compute Savings Plans, EC2 Instance Savings Plans, and Amazon SageMaker Savings Plans. Compute Savings Plans apply to usage across Amazon EC2, AWS Lambda, and AWS Fargate. The EC2 Instance Savings Plans apply to EC2 usage, and Amazon SageMaker Savings Plans apply to Amazon SageMaker usage.

#### Compute

1. AWS Batch.

    * AWS Batch lets developers, scientists, and engineers efficiently run hundreds of thousands of batch and ML computing jobs while optimizing compute resources, so you can focus on analysing results and solving problems. 

1. Amazon EC2.

    * Elastic Compute Cloud (EC2) is a web service that provides resizable compute capacity in the cloud. It is designed to make web-scale computing easier for developers. It reduces the time required to obtain and boot new server instances to minutes.

    * The following pricing types are available with EC2:
        * **On Demand:** Allows you to pay a fixed rate by the hour (or by the second) with no commitment.
        * **Reserved:** Provides you with a capacity reservation, and offers a significant discount on the hourly charge for an instance. Contract terms are 1-year or 3-year terms. Up to a 72% discount on the hourly charge.
        * **Spot:** Enables you to bid whatever price you want for instance capacity, providing for even greater savings if your applications have flexible start and end times. If your instance is terminated by Amazon, you will not be charged for a partial hour of usage. However, if you terminate the instance yourself, you will be changed for any hour in which the instance ran. Up to a 90% discount.
        * **Dedicated Hosts:** Physical EC2 server dedicated for your use. Helps reduce your costs by allowing you to use your existing server-bound software licenses.

    * Spot instances save up to 90% of the cost of on-demand instances. They are useful for any type of computing where you don't need persistent storage. A spot fleet is a collection of spot instances and, optionally, on-demand instances. You can block spot instances from terminating by using spot block.

    * Termination protection is turned off by default, it must be turned on. On an EBS-backed instance, the default action is for the root EBS volume to be deleted when the instance is terminated. However, other volumes will not be deleted by default. EBS root volumes and additional volumes can be encrypted. You can also use a third party tool (such as bitlocker) to encrypt the root volume, or this can be done when creating AMI's.

    * Regarding Security Groups:
        * All inbound traffic is blocked by default.
        * All outbound traffic is allowed.
        * Changes to Security Groups take effect immediately
        * You can have any number of EC2 instances within a security group.
        * You can have multiple security groups attached to EC2 instances.
        * Security Groups are stateful.
        * If you create an inbound rule allowing traffic in, that traffic is automatically allowed back out again.
        * You cannot block specific IP addresses using Security Groups, instead use Network Access Control Lists.
        * You can specify allow rules, but not deny rules.

    * Regarding network devices available in EC2:
        * **Elastic Network Interface (ENI):** A virtual network card. Used for basic networking. If you need a separate networks for production and logging, you can use multiple ENIs for each network.
        * **Enhanced Networking (EN):** Uses single root I/O virtualisation (SR-IOV) to provide high-performance networking capabilities on supported instance types. Used for when you need speeds between 10 Gbps and 100 Gbps. This is for reliable, high throughput.
        * **Elastic Fabric Adapter:** A network device that you can attach to your Amazon EC2 instance to accelerate High Performance Computing (HPC) and machine learning applications. Used for when you need to accelerate High Performance Computing (HPC) and machine learning applications, or you need to do an OS bypass.

    * Regarding EC2 Hibernate:
        * Hibernate preserves in-memory RAM on persistent storage (EBS). It is faster to boot because you do not need to reload the operating system.
        * Instance RAM must be less than 150 GB.
        * Instance families include C3, C4, C5, M3, M4, M5, R3, R4 and R5.
        * Hibernate is available for Windows, Amazon Linux 2 AMI, and Ubuntu.
        * Hibernate is available for on-demand instances and reserved instances.
        * Instances can't be hibernated for more than 60 days.

    * Roles are far more secure than storing your access key and secret access key on individual EC2 instances (in the .aws directory). Roles are easier to manage. Roles can be assigned to an EC2 instance after it is created using both the console and command line. Roles are universal, you can use them in any region.

    * A bootstrap script runs with administrator privileges on EC2 instance start-up. It is configured in the "User data" section on instance creation.

    * Metadata can be queried to get information about an instance:
        ```shell
        curl http://<ip>/latest/meta-data/
        curl http://<ip>/latest/user-data/
        ```

    * EC2 instances can be grouped in different placement groups:
        * **Clustered Placement Group:** For low latency and high network throughput, instances are collocated in the same AZ.
        * **Spread Placement Group:** For critical EC2 instances where you want each instance on separate pieces of hardware. Can span multiple AZs.
        * **Partitioned Placement Group:** As for Spread Placement Group but you can have multiple instances for each piece of hardware. Can span multiple AZs.

    * A placement group name must be unique within your AWS account. Only certain types of instances can be launched in a placement group. AWS recommends homogenous instances within clustered placement groups. Placement groups cannot be merged, but instances can be moved into a placement group if it is in a stopped state. The move can currently only be done with the AWS CLI or an AWS SDK, the console does not support it.

1. Amazon EC2 Auto Scaling.

    * Amazon EC2 Auto Scaling helps you maintain application availability and allows you to automatically add or remove EC2 instances according to conditions you define. You can use the fleet management features of EC2 Auto Scaling to maintain the health and availability of your fleet. You can also use the dynamic and predictive scaling features of EC2 Auto Scaling to add or remove EC2 instances. Dynamic scaling responds to changing demand and predictive scaling automatically schedules the right number of EC2 instances based on predicted demand. Dynamic scaling and predictive scaling can be used together to scale faster.

1. AWS Elastic Beanstalk.

    * Easy-to-use all in one service for deploying and scaling web applications and services developed with a variety of supported languages.

1. AWS Outposts.

    * AWS Outposts is a family of fully managed solutions delivering AWS infrastructure and services to virtually any on-premises or edge location for a truly consistent hybrid experience. Outposts solutions allow you to extend and run native AWS services on premises, and is available in a variety of form factors, from 1U and 2U Outposts servers to 42U Outposts racks, and multiple rack deployments.

    * With AWS Outposts, you can run some AWS services locally and connect to a broad range of services available in the local AWS Region. Run applications and workloads on premises using familiar AWS services, tools, and APIs. Outposts supports workloads and devices requiring low latency access to on-premises systems, local data processing, data residency, and application migration with local system interdependencies. 

1. AWS Serverless Application Repository.

    * The AWS Serverless Application Repository is a managed repository for serverless applications. It enables teams, organizations, and individual developers to store and share reusable applications, and easily assemble and deploy serverless architectures in powerful new ways. Using the Serverless Application Repository, you don't need to clone, build, package, or publish source code to AWS before deploying it. Instead, you can use pre-built applications from the Serverless Application Repository in your serverless architectures, helping you and your teams reduce duplicated work, ensure organizational best practices, and get to market faster.

1. VMware Cloud on AWS.

    * VMware Cloud on AWS provides dedicated, single-tenant cloud infrastructure with support multiple SDDC per organization, with up to 16 hosts per cluster, delivered on the next-generation bare metal AWS infrastructure based on the latest Amazon EC2 Storage Optimized high I/O instances and featuring low-latency Non-Volatile Memory Express (NVMe) based SSDs.

1. AWS Wavelength.

    * AWS Wavelength embeds AWS compute and storage services within 5G networks, providing mobile edge computing infrastructure for developing, deploying, and scaling ultra-low-latency applications.

#### Containers

1. Amazon Elastic Container Registry (Amazon ECR).

    * Amazon ECR is a fully managed container registry offering high-performance hosting, so you can reliably deploy application images and artifacts anywhere.

1. Amazon Elastic Container Service (Amazon ECS).

    * ECS can manage thousands of containers. It will appropriately place the containers and keep them online.

    * Containers are appropriately registered with the load balancers as they come online and go offline.
    
    * Containers can have individual roles attached to them, making security a breeze.
    
    * It is extremely easy to setup and scale to handle any workload.    

1. Amazon ECS Anywhere.

    * Amazon Elastic Container Service (ECS) Anywhere is a feature of Amazon ECS that enables you to easily run and manage container workloads on customer-managed infrastructure. 

    * ECS Anywhere builds upon the ease and simplicity of Amazon ECS to provide a consistent tooling and API experience across your container-based applications. Whether on-premises or in the cloud, you'll have similar cluster management, workload scheduling, and monitoring you've come to know from Amazon ECS.

1. Amazon Elastic Kubernetes Service (Amazon EKS).

    * AWS-managed version of Kubernetes (which is open-source).

    * EKS is best used when you're not all in on AWS and want to run the container on-premises. It is more work to configure and integrate with AWS.

1. Amazon EKS Anywhere.

    * Amazon EKS Anywhere is a new deployment option for Amazon EKS that allows customers to create and operate Kubernetes clusters on customer-managed infrastructure, supported by AWS. Customers can now run Amazon EKS Anywhere on their own on-premises infrastructure on bare metal servers or using VMware vSphere, with support for more deployment targets coming soon.

1. Amazon EKS Distro.

    * Amazon EKS Distro is a Kubernetes distribution built and maintained by AWS and used by Amazon Elastic Kubernetes Service (EKS), that makes it easy to create reliable and secure clusters.

#### Database

1. Amazon Aurora.

    * Aurora is Amazon's proprietary relational database which is MySQL and PostgreSQL-compatible. It has 5x better performance than MySQL and 3x better than PostgresSQL.

    * 2 copies of your data are contained in each AZ, with a minimum of 3 AZs. This means there is a total of 6 copies of your data.

    * You can share Aurora snapshots with other AWS accounts.

    * 3 types of replicas available: Aurora replicas, MySQL replicas, and PostgreSQL replicas. Automated failover is only available with Aurora replicas.

    * Aurora has automated backups turned on by default. You can also take snapshots with Aurora. You can share these snapshots with other AWS accounts.

1. Amazon Aurora Serverless.

    * Amazon Aurora Serverless is a serverless database cluster that automatically starts up, shuts down, and scales capacity up or down based on your application's needs.

    * Use Amazon Aurora Serverless if you want a simple, cost-effective option for infrequent, intermittent, or unpredictable workloads.

1. Amazon DocumentDB (with MongoDB compatibility).

    * Amazon DocumentDB is a scalable, highly durable, and fully managed database service for operating mission-critical MongoDB workloads.

1. Amazon DynamoDB.

    * Amazon DynamoDB is a fast and flexible non-relational database service for any scale. DynamoDB enables customers to offload the administrative burdens of operating and scaling distributed databases to AWS so that they don’t have to worry about hardware provisioning, setup and configuration, throughput capacity planning, replication, software patching, or cluster scaling.

    * Key facts about DynamoDB:
        * Stored on SSD.
        * Spread across 3 geographically distinct data centres.
        * Eventually consistent reads (default).
        * Strongly consistent reads.

    * Eventually consistent will achieve consistency within a second. Strongly consistent will achieve consistency instantly.

    * DynamoDB transactions provide developers ACID properties across 1 or more tables within a single AWS account and region.

    * Point-in-Time Recovery (PITR) can protect against accidental writes or deletes. You can restore to any point in the last 35 days and up to 5 minutes in the past. Not enabled by default.

    * DynamoDB streams provide a time-ordered sequence of item-level changes in a table. Stored for 24 hours. The stream includes events such as inserts, updates, and deletes. Can be combined with Lambda function for functionality like stored procedures.

    * Global Tables provides managed multi-master, multi-region replication. It is based on DynamoDB streams. Replication latency is under 1 second.

    * DynamoDB Accelerator (DAX) is a caching solution that can reduce DynamoDB response times from milliseconds to microseconds. The cache is highly available and lives inside the VPC you specify. You determine the node size and count for the cluster, TTL for the data, and maintenance windows for changes and updates.

1. Amazon ElastiCache.

    * ElastiCache is a managed version of 2 open-source technologies: Memcached and Redis. Memcached is a simple database caching solution with no failover, backups, or multi-AZ support. Redis is a caching solution but can also function as a standalone database, which can provide backups, failover, and multi-AZ support.

1. Amazon Keyspaces (for Apache Cassandra).

    * Amazon Keyspaces (for Apache Cassandra) is a scalable, highly available, and managed Apache Cassandra–compatible database service. With Amazon Keyspaces, you can run your Cassandra workloads on AWS using the same Cassandra application code and developer tools that you use today. You don’t have to provision, patch, or manage servers, and you don’t have to install, maintain, or operate software

1. Amazon Neptune.

    * Amazon Neptune is a fast, reliable, fully managed graph database service that makes it easy to build and run applications that work with highly connected datasets. The core of Amazon Neptune is a purpose-built, high-performance graph database engine optimized for storing billions of relationships and querying the graph with milliseconds latency.

1. Amazon Quantum Ledger Database (Amazon QLDB).

    * Amazon Quantum Ledger Database (QLDB) is a fully managed ledger database that provides a transparent, immutable, and cryptographically verifiable transaction log.

1. Amazon RDS.

    * RDS is for OLTP (Online Transaction Processing) workloads. This involves small transactions, like customer orders, banking transactions, payments, and booking systems.

    * Online Analytical Processing (OLAP) should use Redshift. This is for tasks such as analysing large amounts of data, reporting, and sales forecasting.

    * Amazon Relational Database Service (Amazon RDS) is a managed service that makes it easy to set up, operate, and scale a relational database in the cloud. Amazon RDS gives you access to the capabilities of a familiar MySQL, MariaDB, Oracle, SQL Server, or PostgreSQL database.

    * Multi-AZ provides an exact copy of your production database in another AZ. Used for disaster recovery. In the event of a failure, RDS will automatically failover to the standby instance.

1. Amazon Redshift.

    * Amazon Redshift is a fully managed, petabyte-scale data warehouse service in the cloud. You can start with just a few hundred gigabytes of data and scale to a petabyte or more. This allows you to use your data to gain new insights for your business and customers.

1. Amazon Timestream.

    * Amazon Timestream is a fast, scalable, and serverless time series database service for IoT and operational applications that makes it easy to store and analyse trillions of events per day up to 1,000 times faster and at as little as 1/10th the cost of relational databases. Amazon Timestream saves you time and cost in managing the lifecycle of time series data by keeping recent data in memory and moving historical data to a cost optimized storage tier based upon user defined policies.

    * Amazon Timestream’s purpose-built query engine lets you access and analyse recent and historical data together, without needing to specify explicitly in the query whether the data resides in the in-memory or cost-optimized tier. Amazon Timestream has built-in time series analytics functions, helping you identify trends and patterns in your data in near real-time. Amazon Timestream is serverless and automatically scales up or down to adjust capacity and performance, so you don’t need to manage the underlying infrastructure, freeing you to focus on building your applications.

#### Developer Tools

1. AWS X-Ray.

    * AWS X-Ray provides a complete view of requests as they travel through your application and filters visual data across payloads, functions, traces, services, APIs, and more with no-code and low-code motions.

#### Front-End Web and Mobile

1. AWS Amplify.

    * AWS Amplify is a complete solution that lets frontend web and mobile developers easily build, ship, and host full-stack applications on AWS, with the flexibility to leverage the breadth of AWS services as use cases evolve. No cloud expertise needed.

1. Amazon API Gateway.

    * API Gateway is a fully managed service that makes it easy for developers to create, publish, maintain, monitor, and secure APIs at any scale.

    * API Gateway supports versioning of your API.

    * API Gateway stops you from baking credentials into your code.

1. AWS Device Farm.

    * AWS Device Farm is an application testing service that lets you improve the quality of your web and mobile apps by testing them across an extensive range of desktop browsers and real mobile devices; without having to provision and manage any testing infrastructure. The service enables you to run your tests concurrently on multiple desktop browsers or real devices to speed up the execution of your test suite and generates videos and logs to help you quickly identify issues with your app.

1. Amazon Pinpoint.

    * Amazon Pinpoint offers marketers and developers one customizable tool to deliver customer communications across channels, segments, and campaigns at scale.

#### Machine Learning

1. Amazon Comprehend.

    * Amazon Comprehend is a natural-language processing (NLP) service that uses machine learning to uncover valuable insights and connections in text. Used for sentiment analysis.

1. Amazon Forecast.

    * Amazon Forecast is a time-series forecasting service based on machine learning (ML) and built for business metrics analysis.

1. Amazon Fraud Detector.

    * Amazon Fraud Detector is a fully managed service enabling customers to identify potentially fraudulent activities and catch more online fraud faster.

1. Amazon Kendra.

    * Amazon Kendra is an intelligent enterprise search service that allows users to search across different content repositories with built-in connectors. Used to build an intelligence search based on unstructured text.

1. Amazon Lex.

    * Amazon Lex is a fully managed artificial intelligence (AI) service with advanced natural language models to design, build, test, and deploy conversational interfaces in applications.

1. Amazon Polly.

    * Amazon Polly uses deep learning technologies to synthesize natural-sounding human speech, so you can convert articles to speech. With dozens of lifelike voices across a broad set of languages, use Amazon Polly to build speech-activated applications.

1. Amazon Rekognition.

    * Amazon Rekognition offers pre-trained and customizable computer vision (CV) capabilities to extract information and insights from your images and videos.

1. Amazon SageMaker.

    * Amazon SageMaker is a fully managed machine learning service. With SageMaker, data scientists and developers can quickly and easily build and train machine learning models, and then directly deploy them into a production-ready hosted environment.

1. Amazon Textract.

    * Amazon Textract is a machine learning (ML) service that automatically extracts text, handwriting, and data from scanned documents. It goes beyond simple optical character recognition (OCR) to identify, understand, and extract data from forms and tables. Today, many companies manually extract data from scanned documents such as PDFs, images, tables, and forms, or through simple OCR software that requires manual configuration (which often must be updated when the form changes). 

    * To overcome these manual and expensive processes, Textract uses ML to read and process any type of document, accurately extracting text, handwriting, tables, and other data with no manual effort. You can quickly automate document processing and act on the information extracted, whether you’re automating loans processing or extracting information from invoices and receipts. Textract can extract the data in minutes instead of hours or days. Additionally, you can add human reviews with Amazon Augmented AI to provide oversight of your models and check sensitive data.

1. Amazon Transcribe.

    * Powered by deep learning technologies, Amazon Transcribe is a fully managed and continuously trained automatic speech recognition service that automatically generates time-stamped text transcripts from audio files.

1. Amazon Translate.

    * Amazon Translate is a neural machine translation service that delivers fast, high-quality, affordable, and customizable language translation. Neural machine translation is a form of language translation automation that uses deep learning models to deliver more accurate and more natural sounding translation than traditional statistical and rule-based translation algorithms.

#### Management and Governance

1. AWS Auto Scaling.

    * AWS Auto Scaling offers a centralized place to manage configurations for a wider range of scalable resources, such as EC2 instances, Amazon Elastic Container Service (ECS), Amazon DynamoDB tables or Amazon Relational Database Aurora read replicas.

1. AWS CloudFormation.

    * CloudFormation allows you to provision resources quickly and consistently, and manage them throughout their lifecycles, by treating infrastructure as code.

    * Declarative programming language which supports JSON or YAML formatting.

1. AWS CloudTrail.

    * CloudTrail increases visibility into your user and resource activity by recording AWS Management Console actions and API calls.

    * Useful for after-the-fact incident investigation, near real-time intrusion detection (when integrated with Lambda functions), and industry and regulatory compliance.

1. Amazon CloudWatch.

    * CloudWatch monitors your AWS resources and the applications you run on AWS in real time. You can use CloudWatch to collect and track metrics, which are variables you can measure for your resources and applications.

    * The CloudWatch home page automatically displays metrics about every AWS service you use. You can additionally create custom dashboards to display metrics about your custom applications and display custom collections of metrics that you choose. Alarms can also be created to notify you when thresholds are hit.

    * CloudWatch with EC2 will monitor events every 5 minutes by default. you can have 1-minute intervals by turning on detailed monitoring.

    * CloudWatch Events help you to respond to state changes in your AWS resources.
    
    * CloudWatch Logs help you to aggregate, monitor, and store logs. If logs need to be stored but not processed, they could go to S3, otherwise they should go to CloudWatch Logs.

    * CloudWatch monitors performance. CloudTrail monitors API calls in the AWS platform.

    * By default, AWS can't see past the hypervisor level for EC2 instances. This means custom events need to be created for things such as memory or disk usage.

    * CloudWatch Logs Insights allows you to interrogate logs with SQL.

1. AWS Command Line Interface (AWS CLI).

    * The AWS Command Line Interface (AWS CLI) is a unified tool to manage your AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.

1. AWS Compute Optimizer.

    * AWS Compute Optimizer recommends optimal AWS Compute resources for your workloads to reduce costs and improve performance by using machine learning to analyse historical utilization metrics. Over-provisioning compute (Amazon EC2 and ASGs) can lead to unnecessary infrastructure cost and under-provisioning compute can lead to poor application performance.
 
    * Compute Optimizer helps you choose the optimal Amazon EC2 instance types, including those that are part of an Amazon EC2 Auto Scaling group, based on your utilization data. 

1. AWS Config.

    * Config is an inventory management and control tool. It allows you to show the history of your infrastructure along with creating rules to make it conform to the best practices you've laid out. Config also offers the ability to remediate problems using Automation documents.

1. AWS Control Tower.

    * AWS Control Tower provides the easiest way to set up and govern a secure, multi-account AWS environment, called a landing zone. It creates your landing zone using AWS Organizations, bringing ongoing account management and governance as well as implementation best practices based on AWS’s experience working with thousands of customers as they move to the cloud.

1. AWS License Manager.

    * License Manager makes it easier for you to manage your software licenses from vendors, such as Microsoft, SAP, Oracle, and IBM, across AWS and your on-premises environments.

1. Amazon Managed Grafana.

    * Amazon Managed Grafana is a fully managed service for Grafana, a popular open-source analytics platform that lets you query, visualize, understand, and receive alerts about your metrics no matter where they are stored.

1. Amazon Managed Service for Prometheus.

    * Amazon Managed Service for Prometheus is a Prometheus-compatible service that monitors and provides alerts on containerized applications and infrastructure at scale. The service is integrated with Amazon Elastic Kubernetes Service (EKS), Amazon Elastic Container Service (ECS), and AWS Distro for OpenTelemetry.

1. AWS Management Console.

    * The AWS Management Console is a web application that comprises and refers to a broad collection of service consoles for managing AWS resources.

1. AWS Organizations.

    * AWS Organizations is a free governance tool that allows you to create and manage multiple AWS accounts. With it, you can control your accounts from a single location rather than jumping from account to account.

    * It is best practice to create a specific account dedicated to logging. CloudTrail supports log aggregation. You can then apply Service Control Policies (SPCs) to restrict anyone from making changes to them.

1. AWS Personal Health Dashboard.

    * The AWS Health Dashboard is the single place to learn about the availability and operations of AWS services. You can view the overall status of AWS services, and you can sign in to view personalized communications about your AWS account or organization. Your account view provides deeper visibility into resource issues, upcoming changes, and important notifications.

1. AWS Proton.

    * AWS Proton introduces service components, a new feature that allows developers complement the standard infrastructure of Proton templates with additional resources for their services. Platform engineers use Proton to define the core infrastructure of their services and keep it consistent and updated across services, and now with components developers can complement that core infrastructure with the additional resources they need to meet the needs of their application. Proton components enable platform engineers to expand the use cases they support without having to drastically increase the number of templates that they manage.

    * AWS Proton offers IaC provisioning and deployment of serverless/container architectures.

1. AWS Service Catalog.

    * AWS Service Catalog lets you centrally manage deployed IT services, applications, resources, and metadata to achieve consistent governance of your infrastructure as code (IaC) templates. With AWS Service Catalog, you can meet your compliance requirements while making sure your customers can quickly deploy the approved IT services they need.

    * AWS Service Catalog provides catalogs of preapproved services as CloudFormation templates.

1. AWS Systems Manager.

    * Provides a suite of tools designed to give you the ability to easily patch, update, manage, and configure your EC2 instances along with on-premises infrastructure.

1. AWS Trusted Advisor.

    * Trusted Advisor is a fully managed best-practice auditing tool. It will scan 5 different parts of your account and look for places where you could improve your adoption of the recommended best practices provided by AWS.

    * To get the most useful checks (around cost), you'll need a Business or Enterprise Support plan.

    * Trusted Advisor should be combined with Lambda and EventBridge to automatically resolve issues.

1. AWS Well-Architected Tool.

    * The AWS Well-Architected Tool is designed to help you review the state of your applications and workloads against architectural best practices, identify opportunities for improvement, and track progress over time.

#### Media Services

1. Amazon Elastic Transcoder.

    * Amazon Elastic Transcoder manages all aspects of the media transcoding process for you transparently and automatically.

1. Amazon Kinesis Video Streams.

    * Amazon Kinesis Video Streams makes it easy to securely stream video from connected devices to AWS for analytics, machine learning (ML), playback, and other processing. Kinesis Video Streams automatically provisions and elastically scales all the infrastructure needed to ingest streaming video data from millions of devices.

#### Networking and Content Delivery

1. Amazon CloudFront.

    * CloudFront is a Content Delivery Network (CDN) that works in conjunction with other services to provide developers with a simple way to distribute content to end users.

    * This service is useful for companies with a need for higher response times and large file content that want to distribute these files to a sizeable number of users. Once content is put in an origin server, like an Amazon Simple Storage Service bucket or an Elastic Compute Cloud instance, it’s pushed out to multiple CloudFront servers as content is requested.

    * An **Edge Location** is the location where content will be cached. This is separate to an AWS Region or AZ. Edge locations are not just read only, they can be written to as well. Objects are cached for the life of the Time to Live (TTL). Cached objects can be cleared but you will be charged.

    * The **Origin** is the origin of all the files that the CDN will distribute. This can be an S3 Bucket, an EC2 Instance, an Elastic Load Balancer, or Route 53.

    * The **Distribution** is the name given to the CDN which consists of a collection of Edge Locations.

    * A **Web Distribution** is typically for websites and a **RTMP** is used for media streaming.

    * Use signed URLs or cookies when you want to secure content so that only the people you authorise are able to access it. A signed URL is for individual files with 1 file corresponding to 1 URL. A signed cookie is for multiple files with 1 cookie corresponding to multiple files. If your origin is EC2, then use CloudFront. If your origin is S3, then use an S3 signed URL.

    * CloudFront is the only option to add HTTPS to a static website being hosted in S3.

1. AWS Direct Connect.

    * Direct Connect directly connects your data centre to AWS. Useful for high-throughput workloads that require a stable and reliable secure connection.

1. Elastic Load Balancing (ELB).

    * There are 3 types of ELBs:
        * **Application Load Balancers:** Functions at the seventh layer (application) of the OSI model. A listener checks for connection requests from clients, using the protocol and port you configure. Rules determine how the load balancer routes requests to its registered targets. Each rule consists of a priority, one or more actions, and one or more conditions. Each target group routes requests to one or more register targets, such as EC2 instances, using the protocol and port number you specify. Application Load Balancers only support HTTP and HTTPS. To use a HTTPS listener, you must deploy at least one TLS server certificate on your load balancer. The certificate is used to decrypt requests from clients before sending them to targets.
        * **Network Load Balancer:** Functions at the 4th layer (network) of the OSI model. Used when you need extreme performance. Other use cases are when you need protocols not supported by an ALB. NLBs can decrypt traffic, but you will need to install the certificate on the load balancer.
        * **Classic Load Balancer:** The classic ELB works at both layer 4 and layer 7 and is a legacy load balancer.

    * Sticky sessions enable your users to stick to the same EC2 instance. It can be useful if you are storing information locally to that instance. If you experience a scenario where you remove an EC2 instance from a pool, but the load balancer continues to direct traffic to that EC2 instance, it can be solved by disabling sticky sessions.

    * Deregistration Delay allows Load Balancers to keep existing connections open if the EC2 instances are de-registered or become unhealthy. This enables the load balancer to complete in-flight requests made to instances that are de-registering or unhealthy.

    * You can use health checks to route your traffic to instances or targets that are healthy.

1. AWS Global Accelerator.

    * Global Accelerator is a networking service that sends your users' traffic through AWS's global network infrastructure. It can increase performance and help deal with IP caching. This solves the problem that can arise if some of your architecture fails and the IP changed behind the scenes, causing users to not be able to access the proper endpoint.

1. AWS PrivateLink.

    * AWS PrivateLink enables peering VPCs to tens, hundreds, or thousands of customers VPCs. Does not require VPC peering, route tables, NAT Gateways, Internet Gateways, etc. Requires a Network Load Balance on the service VPC and an Elastic Network Interface (ENI) on the customer VPC.

1. Amazon Route 53.

    * An alias is an AWS concept and should be chosen over CNAME.

    * Common DNS record types:
        * Start of Authority (SOA) Records. Stores the name of the server that supplied the data for the zone, the administrator, the current version of the data, and the default number of seconds for the time-to-live file on resource records.
        * Canonical Name (CNAME). Used to resolve one domain name to another. For example, you may have a mobile website with the domain name http://m.acloud.guru that is used for when users browse to your domain name on their mobile devices.
        * Name Server (NS) Records. Used by top-level domain servers to direct traffic to the content DNS server that contains the authoritative DNS records.
        * A Records. Fundamental type of DNS record. Used to translate the name of the domain to an IP address.
        * Alias Records. Used to map resource record sets in your hosted zone to load balancers, CloudFront distributions, or S3 buckets that are configured as websites. Work like a CNAME record in that you can map one DNS name to another "target" DNS name.

    * Time to Live (TTL) is the length that a DNS record is cached on either the resolving server or the user's own local PC.

    * Routing policies available in Route 53:
        * **Simple Routing:** You can only have one record with multiple IP addresses. If you specify multiple values, Route 53 returns all values to the user in a random order.
        * **Weighted Routing:** Route 53 will send certain percentage of traffic to AZs, regions etc.
        * **Latency-Based Routing:** Route53 will send traffic to the lower latency option.
        * **Failover Routing:** An Active Passive setup which will Failover automatically.
        * **Geolocation Routing:** Traffic will be sent based on the originating location.
        * **Geoproximity Routing (Traffic Flow Only):** Lets Route 53 route traffic to your resources based on the geographic location of your users and resources. You can also optionally choose to route traffic by specifying a value known as a bias. The bias expands or shrinks the size of the geographic region from which traffic is routed to a resource. You must use Route 53 traffic flow.
        * **Multivalued Answer Routing:** Distributes DNS responses across multiple IP addresses.

    * You can buy domain names directly with AWS. It can take up to 3 days to register depending on the circumstances.

    * Health checks can be set on individual record sets. If a record fails, it will be removed from Route 53 until it passes. You can set SNS notifications to alert you about failed health checks.

1. AWS Transit Gateway.

    * AWS Transit Gateway works with Direct Connect as well as VPN connections. It supports IP multicast (which is not supported by any other AWS service). Mostly used for audio and video distribution.

1. Amazon VPC.

    * A Virtual Private Cloud (VPC) is a virtual network dedicated to a single AWS account. It is logically isolated from other virtual networks in the AWS cloud.

    * It consists of internet gateways (or virtual private gateways), route tables, network access control lists, subnets, and security groups.

    * 1 subnet is always in 1 AZ.

    * NAT Gateways are redundant inside the AZ. They start at 5 Gbps and scales to 45 Gbps. No patching is required. They are not associated with any Security Groups. They are automatically assigned a public IP address when created.

    * To create an AZ-independent architecture, create a NAT gateway in each AZ and configure your routing to ensure resources use the NAT gateway in the same AZ.

    * Security Groups are stateful - if you send a request from your instance, the response traffic for that request is allowed to flow regardless of inbound Security Group rules.

    * Network ACLs:
        * **Default:** Allows all outbound and inbound traffic.
        * **Custom:** Denies all outbound and inbound traffic until you add rules.

    * You can associate a network ACL with multiple subnets; however, a subnet can be associated with only 1 network ACL at a time. Network ACLs contain a numbered list of rules that are evaluated in order, starting with the lowest numbered rule.

    * Network ACLs are stateless; responses to allowed inbound traffic are subject to the rules for outbound traffic (and vice versa).

    * Each subnet in your VPC must be associated with a network ACL. If you do not explicitly associate a subnet with a network ACL, it will automatically be associated with the default network ACL.

    * Blocking IP addresses is done using network ACLs, and not Security Groups.

1. AWS VPN.

    * AWS Virtual Private Network solutions establish secure connections between your on-premises networks, remote offices, client devices, and the AWS global network. AWS VPN is comprised of two services: AWS Site-to-Site VPN and AWS Client VPN. Each service provides a highly available, managed, and elastic cloud VPN solution to protect your network traffic.

#### Security, Identity, and Compliance

1. AWS Artifact.

    * AWS Artifact is your go-to, central resource for compliance-related information that matters to you. It provides on-demand access to AWS’ security and compliance reports and select online agreements. Reports available in AWS Artifact include our Service Organization Control (SOC) reports, Payment Card Industry (PCI) reports, and certifications from accreditation bodies across geographies and compliance verticals that validate the implementation and operating effectiveness of AWS security controls. Agreements available in AWS Artifact include the Business Associate Addendum (BAA) and the Nondisclosure Agreement (NDA).

1. AWS Audit Manager.

    * Use AWS Audit Manager to map your compliance requirements to AWS usage data with prebuilt and custom frameworks and automated evidence collection.

1. AWS Certificate Manager (ACM).

    * Certificate Manager allows you to create, manage, and deploy public and private SSL certificates for use with other AWS services. It integrates with other services such as ELB, CloudFront, and API Gateway.

    * Save on cost with public and private certificates being provisioned for free. Automatic renewal and update of the certificate. Removes manual processes such as generating a Certificate Signing Request (CSR).

1. AWS CloudHSM.

    * Provides a dedicated HSM with full control of the underlying hardware and users, groups, keys, etc. No automatic key rotation.

1. Amazon Cognito.

    * Amazon Cognito provides an identity store that scales to millions of users, supports social and enterprise identity federation, and offers advanced security features to protect your consumers and business. Built on open identity standards, Amazon Cognito supports various compliance regulations and integrates with frontend and backend development resources.

1. Amazon Detective.

    * Amazon Detective simplifies the investigative process and helps security teams conduct faster and more effective investigations. With the Amazon Detective prebuilt data aggregations, summaries, and context, you can quickly analyse and determine the nature and extent of possible security issues.

1. AWS Directory Service.

    * Directory Service is a fully managed version of Active Directory. It allows you to offload the painful parts of keeping AD online to AWS while giving you the full control and flexibility AD provides.

    * Managed Microsoft AD is for when we want to migrate everything into AWS. AD Connector is used when you want to leave it on-premises.

1. AWS Firewall Manager.

    * AWS Firewall Manager is a security management service that allows you to centrally configure and manage firewall rules across your accounts and applications in AWS Organizations. As new applications are created, Firewall Manager makes it easier to bring new applications and resources into compliance by enforcing a common set of security rules.

1. Amazon GuardDuty.

    * GuardDuty is a threat detection service that uses machine learning to continuously monitor for malicious behaviour. It will learn what normal behaviour is in your account and identify abnormal or malicious behaviour.

    * GuardDuty updates a database of known malicious domains using external feeds from third parties.

    * Alerts appear in the GuardDuty console and CloudWatch Events.

1. AWS Identity and Access Management (IAM)

    * IAM allows you to manage users and their level of access to the AWS Console.

    * IAM is universal. It does not apply to regions. New users have NO permissions when first created. New users are assigned an Access Key ID & Secret Access Key when first created. These are not the same as a password and you cannot use them to login to the console. You can use these to access AWS is the APIs. You only get to view them once.

    * Multifactor authentication should always be setup on your root account. A password rotation policy can also be created.

1. Amazon Inspector.

    * Inspector is an automated security assessment service that helps improve the security and compliance of applications deployed on AWS.

    * Two types of assessment:
        * **Network Assessment:** Network configuration analysis to check for ports reachable from outside the VPC. Inspector agent is not required.
        * **Host Assessment:** Vulnerable software (CVE), host hardening (CIS Benchmarks), and security best practices. Inspector agent is required.

1. AWS Key Management Service (AWS KMS).

    * KMS is a managed service that makes it easy for you to create and control the encryption keys used to encrypt your data. It integrates with services such as EBS, S3, and RDS to simplify management of encryption.

    * A Customer Managed Key (CMK) is required. AWS can create the CMK, with key material generated within HSMs managed by AWS KMS. You can import your own key material and associate it with a CMK. You can also have the key material generated and used in an AWS CloudHSM cluster as part of the custom key store feature in AWS KMS.

    * Permissions on keys is controlled using the key policy. IAM policies can be used in combination with the key policy to manage all the permissions for your IAM identities in IAM. You can also use grants in combination with the key policy to allow access to the CMK in the key policy, as well as allow users to delegate their access to others. 

1. Amazon Macie.

    * Amazon Macie is a security service which uses Machine Learning (ML) and Natural Language Processing (NLP) to discover, classify and protect sensitive data stored in S3. It can also be used to analyse CloudTrail logs for suspicious API activity. It provides dashboards, reports, and alerting. It is great for PCI-DSS compliance and preventing ID theft.

1. AWS Network Firewall.

    * AWS Network Firewall is a managed service that makes it easy to deploy essential network protections for all your Amazon Virtual Private Clouds (VPCs). Useful to filter network traffic before it reaches your Internet Gateway, or if you require IPS or for any hardware firewall requirements.

1. AWS Resource Access Manager (AWS RAM).

    * RAM is a free service that allows you to share AWS resources with other accounts and within your organisation. RAM allows you to easily share resources rather than having to create duplicate copies in your different accounts.

    * RAM should be used when sharing resources within the same region. VPC peering should be used when sharing across regions.

1. AWS Secrets Manager.

    * Secrets Manager is a service that securely stores, encrypts, and rotates your database credentials and other secrets (API keys, SSH keys etc.). Applications use the Secrets Manager API. Rotating credentials is easy, but when enabled credentials will be rotated immediately. Application instances need to be configured to use Secrets Manager before doing this.

1. AWS Security Hub.

    * AWS Security Hub is a Cloud Security Posture Management (CSPM) service that performs security best practice checks, aggregates alerts, and enables automated remediation.

1. AWS Shield.

    * Free DDoS protection that protects all AWS customers on ELB, CloudFront, and Route 53. Protects against SYN/UDP floods and other Layer 3 and Layer 4 attacks.

    * Shield Advanced provides enhanced protections for your applications against more sophisticated attacks. Offers monitoring of network traffic and active application monitoring to provide near real-time notification of DDoS attacks. Gives 24/7 access to the DDoS Response Team (DRT) to help manage and mitigate DDoS attacks. Can protect against higher fees due to usage spikes from DDoS attacks.

1. AWS Single Sign-On.

    * AWS IAM Identity Center (successor to AWS Single Sign-On) helps you securely create or connect your workforce identities and manage their access centrally across AWS accounts and applications. IAM Identity Center is the recommended approach for workforce authentication and authorization on AWS for organizations of any size and type.

1. AWS WAF.

    * Amazon WAF is a web application firewall that lets you monitor the HTTP and HTTPS requests that are forwarded to Amazon CloudFront, an Application Load Balancer, or API Gateway. AWS WAF also lets you control access to your content.

    * Conditions that can be configured include:
        * The IP addresses that requests originate from.
        * The country that requests originate from.
        * The values in request headers.
        * The strings that appear in requests.
        * The length of requests.
        * The presence of SQL code that is likely to be malicious.
        * The presence of a script that is likely to be malicious.

    * Based on these conditions the application load balancer, CloudFront, or API Gateway will allow content to be received or to give HTTP 403 response.

#### Serverless

1. AWS AppSync.

    * AWS AppSync creates serverless GraphQL and Pub/Sub APIs that simplify application development through a single endpoint to securely query, update, or publish data.

1. AWS Fargate.

    * Fargate is a serverless compute engine for containers that works with both ECS and EKS.

    * EC2 is cheaper, better for long-running containers, multiple containers can share the same host, and you are responsible for the underlying operating system. 

    * Fargate provides no operating system access. You pay based on the resources allocated and time ran. Ideal for short-running tasks. Everything is isolated.

    * Fargate excels over Lambda when you have more consistent workloads, or you need greater level of control by developers. Lambda is great for unpredictable or inconsistent workloads or workloads that can be expressed in a single function.

1. AWS Lambda.

    * Lambda lets you run code without provisioning or managing servers. You pay only for the compute time you consume.

    * When building a Lambda function, you will need to consider:
        * **Runtime:** You will need to pick an available runtime or bring your own. This is the environment the code will run in.
        * **Permissions:** If your Lambda function needs to make an AWS API call, you'll need to attach a role.
        * **Networking:** You can (optionally) define the VPC, subnet, and security groups your functions are a part of.
        * **Resources:** Defining the amount of available memory will allocate how much CPU and RAM your code gets.
        * **Trigger:** What is going to trigger your Lambda function to start?

    * Lambda excels in running small and lightweight function. Lambda can run inside or outside a VPC. You can use up to 10 GB of RAM and 15 minutes of runtime.

#### Storage

1. AWS Backup.

    * Use AWS Backup to back up AWS services, such as EC2, EBS, EFS, Amazon FSx for Lustre, Amazon FSx for Windows File Server, and AWS Storage Gateway.

    * You can use AWS Organizations in conjunction with AWS Backup to back up your different AWS services across multiple AWS accounts.

    * AWS Backup gives you centralised control, letting you automate your backups and define lifecycle policies for your data. You get better compliance, as you can enforce your backup policies, ensure your backups are encrypted, and audit them once complete.

2. Amazon Elastic Block Store (Amazon EBS).

    * EBS provides persistent block storage volumes for your virtual machine drives. It stores data in equally sized blocks and organizes them into a hierarchy like a traditional file system. Each EBS volume is automatically replicated within its AZ to protect from component failure. The volumes are provisioned in size and attached to EC2 instances in a way that’s like the local disk drive on a physical machine.

    * Volumes are virtual hard disks that exist on EBS. You need a minimum of 1 volume per EC2 instance (the root device volume).

    * EBS must be paired with an EC2 instance and will always be in the same availability zone as the EC2 instance. You can change EBS volume sizes on the fly, including changing the size and storage type. When you need a high-performance storage service for a single instance, use EBS.

    * A summary of the EBS SSD types is shown below:
        <p align="center">
        <img src="/res/EBS_SSD_overview.JPG">
        </p>

    * A summary of the EBS SSD types is shown below:
        <p align="center">
        <img src="/res/EBS_HDD_overview.JPG">
        </p>

    * Regarding Snapshots:
        * Snapshots exist on S3.
        * Snapshots are point in time copies of volumes.
        * Snapshots are incremental, only the blocks that have changed since your last snapshot are moved to S3.
        * To create a snapshot for EBS volumes that serve as root devices, you should stop the instance before taking the snapshot. A snapshot can be taken while the instance is running (although it is recommended to stop the instance).
        * You can create Amazon Machine Images (AMI's) from Snapshots.
        * To move an EC2 volume from one AZ to another, take a snapshot of it, create an AMI from the snapshot and then use the AMI to launch the EC2 instance in a new AZ.
        * To move an EC2 volume from one region to another, take a snapshot of it, create an AMI from the snapshot and then copy the AMI from one region to the other. Then use the copied AMI to launch the new EC2 instance in the new region.
        * Snapshots of encrypted volumes are encrypted automatically.
        * Volumes restored from encrypted snapshots are encrypted automatically.
        * Only unencrypted snapshots can be shared. They can be shared with other AWS accounts or made public.
        * You can now encrypt root device volumes upon creation of the EC2 instance.

    * AMI's are categorised as:
        * **EBS Volumes:** The root device for an instance launch from the AMI is an Amazon EBS volume created from an Amazon EBS snapshot.
        * **Instance Store Volumes:** The root device for an instance launched from the AMI is an instance store volume created from a template stored in Amazon S3.'

    * Instance Store Volumes are sometimes called ephemeral storage. This is because they cannot be stopped, and if the underlying host fails, you will lose your data.

    * EBS backed instances can be stopped. You will not lose the data on this instance if it is stopped. Both EBS Volumes and Instance Store Volumes can be rebooted without data loss.

    * By default, both root volumes will be deleted on termination. However, with EBS volumes, you can tell AWS to keep the root device volume.

1. Amazon Elastic File System (Amazon EFS).

    * Unlike EBS, EFS can be mounted by multiple EC2 instances, meaning many virtual machines may store files within an EFS instance. Its main feature is its scalability. EFS can grow or shrink according to demand, with more and more files being added without disturbing your application or having to provision new infrastructure.

    * EFS may be used whenever you need a shared file storage option for multiple EC2 instances with automatic, high-performance scaling.

    * EFS supports the NFSv4 protocol. You only pay for the storage you use with storage scaling up to petabytes. EFS can support thousands of NFS connections. Data is stored across multiple AZs within a region and EFS provides read after write consistency.

    * Compatible with Linux-based AMI (Windows not currently supported).

1. Amazon FSx (for all types).

    * Amazon FSx for Windows File Server provides a fully managed native Microsoft file system so you can easily move your Windows-based applications that require file storage to AWS. Amazon FSx is built on Windows Server.

    * Amazon FSx runs Windows Server Manage Block (SMB)-based file services. It also supports AD users, access control lists, groups, and security policies, along with Distributed File System (DFS) namespaces and replication.

    * Amazon FSx for Lustre is a fully managed file system that is optimised for compute-intensive workloads, such as high-performance computing, machine learning, media data processing workflows, and Electronic Design Automation (EDA).

1. Amazon S3.

    * Amazon S3 (Simple, Storage, Service) is an object storage system, designed to provide archiving and data control options and to interface with other services beyond EC2. It’s also useful for storing static html pages and shared storage for applications.

    * S3 is good at storing long-term data due to its archiving system. Things like reports and records, which may go unused for years, can be stored on S3 at a lower cost than the other two storage services discussed.

    * Files can be from 0 Bytes to 5 TB. Files are stored in Buckets which are basically folders. S3 is a universal namespace. That is, names must be unique globally. This is because a bucket can be accessed at a web address. When uploading a file to an S3 Bucket, a HTTP 200 response is received upon successful completion of the upload.

    * The format of the AWS URL is `https://<region>.amazonaws.com/<bucket>`.

    * Components of the S3 object include:
        * **Key:** The name of the object.
        * **Value:** The data which is made up of a sequence of bytes.
        * **Version ID:** Important for versioning.
        * **Metadata:** Data about data that you are storing.
        * **Access Control Lists:** Permissions of the object.
        * **Torrent:** 

    * S3 has read after write consistency for PUTS of new objects, and eventual consistency for overwrite PUTS and DELETES. This means that new files will be instantly readable after writing, but there may be a small delay to read the correct version after updating an existing file.

    * S3 has the following availability guarantees:
        * Built for 99.99% with a guarantee of 99.9%.
        * 99.99999999999% (11 9s) durability.

    * S3 has the following features:
        * Tiered Storage.
        * **Lifecycle Management:** Automates moving your objects between the different storage tiers. Can be used in conjunction with versioning.
        * **Versioning:** Stores all versions of an object (including all writes and even if you delete an object). Once enabled, versioning cannot be disabled, only suspended.
        * Encryption.
        * MFA Required for Delete.
        * Secure data using Access Control Lists and Bucket Policies.

    * S3 Storage Classes:
        * **S3 Standard:** 99.99% availability and 99.999999999% durability. Data is stored redundantly across multiple devices and in multiple facilities (>=3 AZs).
        * **S3 - IA (Infrequently Accessed):** For data that is accessed less frequently, but requires rapid access when needed. Lower fee than S3, but you are charged a retrieval fee.
        * **S3 One Zone - IA:** Like IA but you do not require multiple Availability Zone data resilience. This is 20% less than regular S3-IA. Great for long-lived, infrequently accessed, non-critical data.
        * **S3 - Intelligent Tiering:** Designed to optimise costs by automatically moving data to the most cost-effective access tier, without performance impact or operational overhead.
        * **Glacier Instant Retrieval:** Long-term data archiving with instance retrieval time. Retrieval fee applies.
        * **Glacier Flexible Retrieval:** Archive data that does not require immediate access but needs flexibility to retrieve larger sets of data at no cost (e.g. DR). Can be minutes or up to 12 hours. Retrieval fee applies.
        * **Glacier Deep Archive:** Cheapest storage designed for retaining data sets for 7-10 years. Standard retrieval time is 12 hours, and the bulk retrieval time is 48 hours. Retrieval fee applies.

    * A summary of the AWS storage tiers is shown below:
        <p align="center">
        <img src="/res/storage_overview.JPG">
        </p>

    * You are charged for S3 in the following ways:
        * **Storage:** How much data is stored.
        * **Requests:** How many requests are made.
        * **Storage Management Pricing:** The tier of storage.
        * **Data Transfer Pricing:** The cost to transfer objects from different regions.
        * **Transfer Acceleration:** Enables faster transfers of objects to end users and an S3 bucket. Uses Amazon CloudFront’s globally distributed edge locations to route data over an optimised network path.

    * S3 buckets can be configured to create access logs which log all requests made to the S3 bucket.

    * Encryption At Rest is achieved by:
        * **S3 Managed Keys - SSE-S3:** Key managed by Amazon.
        * **AWS Key Management Service, Managed Keys - SSE-KMS:** Key managed by you.
        * **Service Side Encryption With Customer Provided Keys - SSE-C:** Key managed by you.
        * **Client Side:** Encrypting the file before you upload it.

    * S3 Object Lock can be used to store objects in a Write Once, Read Many (WORM) model. It can help you prevent objects from being deleted or modified for a fixed amount of time or indefinitely.

    * S3 Glacier Vault Lock allows you to easily deploy and enforce compliance controls for individual S3 Glacier vaults with a Vault Lock policy. You can specify controls, such as WORM, in a Vault Lock policy and lock the policy from future edits. Once locked, the policy can no longer be changed.

    * Object locks come in governance mode and compliance mode. With governance mode, users can't overwrite or delete an object version or alter its lock settings unless they have special permissions. With compliance mode, a protected object version can't be overwritten or deleted by any user, including the root user in your AWS account.

    * Prefixes are the component of the pathname between the bucket name and the file name. More prefixes result in better performance. You can get 3,500 PUT/COPY/POST/DELETE and 5,500 GET/HEAD requests per second per prefix. This means that if you spread your reads across different prefixes, you can allow more requests per second.

    * Multipart uploads can increase performance when uploading files to S3. This is recommended for files over 100 MB and must be used for any file over 5 GB. S3 byte-range fetches can also increase performance when downloading files from S3.

    * If you are using SSE-KMS to encrypt your objects in S3, keep in mind the KMS limits. Uploading or downloading will count towards the KMS quota. This is region-specific but is either 5,500, 10,000, or 30,000 requests per second. Currently you cannot request a quota increase for KMS.

    * S3 Select is used to retrieve only a subset of data from an object using simple SQL expressions. This allows you to save money on data transfer and increase speed.

    * S3 buckets can be shared across accounts using Bucket Policies and IAM (applies across the entire bucket) or using Bucket ACLs and IAM (individual objects) for programmatic access. To share with console access as well then you can create cross-account IAM roles.
    
    * When using cross region replication, the following should be considered:
        * Versioning must be enabled on both the source and destination buckets.
        * Files in an existing bucket are not replicated automatically.
        * All subsequent updated files will be replicated automatically.
        * Delete markers are not replicated.
        * Deleting individual versions or delete markers will not be replicated

1. Amazon S3 Glacier.

    * S3 Glacier is a secure, durable, and low-cost storage class for data archiving. Retrieval times configurable from minutes to hours.

    * S3 Glacier Deep Archive is the lowest-cost storage class where a retrieval time of 12 hours is acceptable.

1. AWS Storage Gateway.

    * AWS Storage Gateway is a service that connects an on-premises software appliance with cloud-based storage to provide seamless and secure integration between an organisations on-premises IT environment and AWS's storage infrastructure. The service enables you to securely store data to the AWS cloud for scalable and cost-effective storage.

    * AWS Storage Gateway is available for download as a virtual machine (VM) image that you install on a host in your datacentre. Storage Gateway supports either VMware ESXi or Microsoft Hyper-V. Once you've installed your gateway and associated it with your AWS account through the activation process, you can use the AWS Management Console to create the storage gateway option that is right for you.

    * Types of Storage Gateway include:
        * **File Gateway (NFS & SMB):** Files are stored in your S3 buckets, and accessed through a Network File System (NFS) mount point. Ownership, permissions, and timestamps are stored in S3 in the user-metadata of the object associated with the file. Once transferred to S3 they can be managed as native S3 objects.
        * **Volume Gateway (iSCSI):** Presents your applications with disk volumes using the iSCSI block protocol. Data written to these volumes can be asynchronously backed up point-in-time snapshots of your volumes and stored in the cloud as Amazon EBS snapshots. Snapshots are incremental backups that only capture changed blocks. All snapshot storage is compressed to minimise your storage charges. Stored volumes are where the entire dataset is stored on site and is asynchronously backed up to S3. Cached volumes are where the entire dataset is stored on S3 and the most frequently accessed data is cached on site.
        * **Tape Gateway (VTL):** The VTL interface provided lets you leverage your existing tape-based backup application infrastructure to store data on virtual tape cartridges that you create on your tape gateway. Each tape gateway is preconfigured with a media changer and tape drives, which are available to your existing client backup applications as iSCSI devices.

## Practise Questions

### Design Secure Architectures

1. You have been evaluating the NACLs in your company. Most of the NACLs are configured as per the below. If a request comes in, how will it be evaluated?
    ```JSON
    100 All Traffic Allow
    200 All Traffic Deny
    All Traffic Deny *
    ```
    * The request will be allowed. Rules with the lowest numbers are evaluated first and matched immediately even if subsequent rules are not consistent.

1. You have been given an assignment to configure Network ACLs in your VPC. Before configuring the NACLs, you need to understand how the NACLs are evaluated. How are NACL rules evaluated?
    * NACL rules are evaluated by rule number from lowest to highest and executed immediately when a matching rule is found.

1. Your company has gotten back results from an audit. One of the mandates from the audit is that your application, which is hosted on EC2, must encrypt the data before writing this data to storage. It has been directed internally that your solution must leverage an AWS managed hardware security module for the cryptographic keys. Which service could you use to meet this requirement?
    * AWS KMS. You can configure your application to use the KMS API to encrypt all data before saving it to disk. AWS Cloud HSM is not required unless you need to create and manage the Hardware Security Modules (HSMs) that store your encryption keys.

1. You are managing S3 buckets in your organization. This management of S3 extends to Amazon Glacier. For auditing purposes, you would like to be informed if an object is restored to S3 from Glacier. What is the most efficient way you can do this?
    * Configure S3 notifications for restore operations from Glacier. S3 has this capability natively and you don't need to use a Lambda function.

1. You have been evaluating the NACLs in your company. Most of the NACLs are configured the same. How can the last rule be edited?
    ```JSON
    100 All Traffic Allow
    200 All Traffic Deny
    All Traffic Deny *
    ```
    * The last rule cannot be modified or removed.

1. You work in healthcare for an IVF clinic. You host an application on AWS, which allows patients to track their medication during IVF cycles. The application also allows them to view test results, which contain sensitive medical data. You have a regulatory requirement that the application is secure, and you must use dedicated hardware firewalls. What AWS service would support this?
    * AWS Firewall Manager. AWS Firewall Manager is a security management service in a single pane of glass. It is not used to deploy physical firewalls.

1. You have been evaluating the NACLs in your company. Currently, you are looking at the default network ACL. What is true about the default network ACL?
    * You can add or remove rules from the default NACL (except for the DENY rule with the asterix).

1. A small company has nearly 200 users who already have AWS accounts in the company AWS environment. A new S3 bucket has been created which will allow roughly a third of all users access to sensitive information in the bucket. What is the most time efficient way to get these users access to the bucket?
    * Create a new policy which will grant permissions to the bucket. Create a group and attach the policy to that group. Add the users to this group.

1. You have a secure web application hosted on AWS using Application Load Balancers, Auto Scaling, and a fleet of EC2 instances connected to an RDS database. You need to ensure that your RDS database can only be accessed using the profile credentials specific to your EC2 instances (via an authentication token). How can you achieve this?
    * Using IAM database authentication. IAM has database authentication capabilities that would allow an RDS database to only be accessed using the profile credentials specific to your EC2 instances. IAM roles are used to grant access to AWS services from other AWS services. You would be better using IAM database authentication.

### Design Resilient Architectures

1. Due to strict compliance requirements, your company cannot leverage AWS cloud for hosting their Kubernetes clusters, nor for managing the clusters. However, they do want to try to follow the established best practices and processes that the Amazon EKS service has implemented. How can your company achieve this while running entirely on-premises?
    * Run the clusters on-premises using Amazon EKS Distro. Amazon EKS is based on the EKS Distro, which allows you to leverage the best practices and established processes on-premises that Amazon EKS uses in AWS.

1. A financial tech company has decided to begin migrating their applications to the AWS cloud. Currently, they host their entire application using several self-managed Kubernetes clusters. One of their major concerns during this migration is monitoring and collecting system metrics due to the very large-scale deployments that are in place. Your Chief Technology Officer wants to avoid using AWS-proprietary technology-based monitoring services and instead leverage existing, well-known, open-source applications to help meet the monitoring requirements. Which combination of the following AWS services would best fit the company requirements while minimizing operational overhead?
    * AWS Managed Grafana and AWS Managed Service for Prometheus are the best fits. Amazon Managed Grafana offers a fully managed service for infrastructure for data visualizations. You can leverage this service to query, correlate, and visualize operational metrics from multiple sources. Amazon Managed Service for Prometheus is a serverless, Prometheus-compatible monitoring service for container metrics. It is perfect for monitoring Kubernetes clusters at scale.

1. A financial institution has an application that produces huge amounts of actuary data, which is ultimately expected to be in the terabyte range. There is a need to run complex analytic queries against terabytes of structured data, using sophisticated query optimization, columnar storage on high-performance storage, and massively parallel query execution. Which service will best meet this requirement?
    * Redshift is preferred.

1. An application team has decided to leverage AWS for their application infrastructure. The application performs proprietary, internal processes that other business applications utilize for their daily workloads. It is built with Apache Kafka to handle real-time streaming, which virtual machines running the application in docker containers consume the data from. The team wants to leverage services that provide less overhead but also cause the least amount of disruption to coding and deployments. Which combination of AWS services would best meet the requirements?
    * Amazon ECS Fargate and Amazon MSK. Fargate containers offer the least disruptive changes, while also minimizing the operational overhead of managing the compute services. Amazon MSK is meant for applications that currently use or are going to use Apache Kafka for messaging. It allows for managing of control plane operations in AWS.

1. Currently, you are employed as a solutions architect for a large international shipping company. The company is undergoing an IT transformation and they want to create an immutable database, where they can track packages as they are sent around the world. They will need to track what boxes they go in, what trucks they are sent in, and what aircraft or sea containers they are shipped in. The database needs to be immutable and cryptographically verifiable, and they would like to leverage the AWS cloud to achieve this. What database technology would best suit this requirement?
    * Amazon Quantum Ledger Database (QLDB). This is an immutable and cryptographically verifiable database and would be the best solution.

1. You work for an online retailer where any downtime at all can cause a significant loss of revenue. You have architected your application to be deployed on an Auto Scaling Group of EC2 instances behind a load balancer. You have configured and deployed these resources using a CloudFormation template. The Auto Scaling Group is configured with default settings and a simple CPU utilization scaling policy. You have also set up multiple Availability Zones for high availability. The load balancer does health checks against an HTML file generated by script. When you begin performing load testing on your application and notice in CloudWatch that the load balancer is not sending traffic to one of your EC2 instances. What could be the problem?
    * The EC2 instance has failed the load balancer health check. The load balancer will route the incoming requests only to the healthy instances. The EC2 instance may have passed status checks and be considered healthy to the Auto Scaling group, but the ELB may not use it if the ELB health check has not been met. The ELB health check has a default of 30 seconds between checks, and a default of 3 checks before deciding.

1. You are working for a large financial institution and have been tasked with creating a relational database solution to deal with a read-heavy workload. The database needs to be highly available within the Oregon region and quickly recover if an Availability Zone goes offline. Which of the following would you select to meet these requirements?
    * Create a read replica and point your read workloads to the new endpoint RDS provides. Read replicas can be promoted to become a primary database, but this is a manual procedure.'

1. A small development team with very limited AWS knowledge has begun the process of creating and deploying a new frontend application based on React within AWS. The application is simple and does not need any backend processing via traditional databases. The application does, however, require GraphQL interactions to complete the required processing of data. Which AWS service can the team use to complete this?
    * Deploy a GraphQL interface via AWS AppSync. AWS Amplify is for a full stack application.

1. A large fintech company is using a web application that stores its data on Amazon RDS. As a solutions architect, you have been asked to upgrade the web application so that users around the world can access it using an API. The application will need to be able to handle large bursts of traffic in seconds from time to time. What would an ideal solution look like?
    * Create an API using API Gateway and use Lambda to automatically handle the bursts in traffic. Note that RDS does not have Auto Scaling.

1. You are a solutions architect working for a biotech company that has a large private cloud deployment using VMware. You have been tasked to setup their disaster recovery solution on AWS. What is the simplest way to achieve this?
    * Contact your VMware representative to provision dedicated hardware within AWS in which you can deploy vCenter yourself. Note that there is no VMware landing page.

1. You have a web application that is hosted on a series of EC2 instances that have an Application Load Balancer in front of them. You have created a new CloudFront distribution. You then set up its origin to point to your ALB. You need to provide access to hundreds of private files served by your CloudFront distribution. What should you use?
    * CloudFront signed cookies. Signed cookies are useful when you want to access multiple files.

1. You have a subscription website that stores images and videos in S3. You need to distribute that content globally, so you have set up a CloudFront distribution and configured your S3 bucket to only exchange data with your CloudFront distribution. Which CloudFront feature allows you to securely distribute this paid content?
    * CloudFront Signed URLs are commonly used to distribute paid content through dynamically generated signed URLs. Origin Access Identity is used for identification purposes within CloudFront and S3, and it would not be suitable for signed URLs.

1. You have been tasked with designing a strategy for backing up EBS volumes attached to an instance-store-backed EC2 instance. You have been asked for an executive summary on your design, and the executive summary should include an answer to the question, “What can an EBS volume do when snapshotting the volume is in progress”?
    * The volume can be used normally while the snapshot is in progress.

### Design High-Performing Architectures

1. A data company has implemented a subscription service for storing video files. There are two levels of subscription: personal and professional use. The personal users can upload a total of 5 GB of data, and professional users can upload as much as 5 TB of data. The application can upload files of size up to 1 TB to an S3 Bucket. What is the best way to upload files of this size?
    * Multipart upload. The Multipart upload API enables you to upload large objects in parts. You can use this API to upload new large objects or make a copy of an existing object (see Operations on Objects). Multipart uploading is a three-step process: You initiate the upload, you upload the object parts, and after you have uploaded all the parts, you complete the multipart upload. Upon receiving the complete multipart upload request, Amazon S3 constructs the object from the uploaded parts, and you can then access the object just as you would any other object in your bucket. You can list all your in-progress multipart uploads or get a list of the parts that you have uploaded for a specific multipart upload.

1. An Application Load Balancer is fronting an Auto Scaling Group of EC2 instances, and the instances are backed by an RDS database. The Auto Scaling Group has been configured to use the Default Termination Policy. You are testing the Auto Scaling Group and have triggered a scale-in. Which instance will be terminated first?
    * The instance launched from the oldest launch configuration.

1. Your team has provisioned Auto Scaling groups in a single Region. The Auto Scaling groups, at max capacity, would total 40 EC2 instances between them. However, you notice that the Auto Scaling groups will only scale out to a portion of that number of instances at any one time. What could be the problem?
    * There is a vCPU-based On-Demand Instance limit per Region.

1. A team of architects is designing a new AWS environment for a company which wants to migrate to the Cloud. The architects are considering the use of EC2 instances with instance store volumes. The architects realize that the data on the instance store volumes are ephemeral. Which action will not cause the data to be deleted on an instance store volume?
    * A reboot will not cause the data to be deleted.

1. Your application team stores critical data within a third-party SaaS cloud vendor. The data comes from an internal application that runs on Amazon ECS Fargate, which then stores the data within Amazon S3 in a proprietary format. Currently, AWS Lambda functions are triggered via Amazon S3 event notifications to trigger the transfer of data to a SaaS application. Due to resource and time limits, you are exploring other means of completing this workflow of transferring data from AWS to the SaaS solution. Which AWS service offers the most efficiency and has the least operational overhead?
    * AppFlow offers a fully managed service for easily automating the bidirectional exchange of data to SaaS vendors from AWS services like Amazon S3. This helps avoid resource constraints.

1. You work for a large online education company that teaches IT using pre-recorded videos. They want to make their website available to the hearing impaired and need to find a way to convert their videos and audio into speech that they can then display as subtitles. Which AWS service should they use?
    * Amazon Transcribe converts speech to text automatically. You can use this service to generate subtitles.

1. You have landed your dream job at Amazon and are moving to the Alexa team. You will be tasked with product design and improvement. You meet a new colleague who does not come from a tech background, and they would like to know what services make up the Alexa service. Select the correct services.
    * The Alexa suite includes Polly, Transcribe, and Lex.

1. You have just been hired by a large organization which uses many different AWS services in their environment. Some of the services which handle data include: RDS, Redshift, ElastiCache, DynamoDB, S3, and Glacier. You have been instructed to configure a web application using stateless web servers. Which services can you use to handle session state data?
    * DynamoDB, RDS, or ElastiCache can handle session data. Redshift is a data warehouse and not appropriate for handling session data.

1. You company has a local content management system (CMS) using Microsoft Sharepoint that is hosted on-premises. Due to a recent acquisition of another company, you expect traffic to the CMS to more than double in the coming week, so you have decided to migrate the SharePoint server to AWS. You need high performance using a Windows shared file storage. You need a high-performing cloud storage solution that is highly available and can be integrated with Active Directory. What would be the best storage option?
    * Make an Amazon FSx for Windows File System and join this to an Active Directory Domain Controller hosted in AWS.

1. You have a large number of files in S3 and you have been asked to build an index of these files. To do this, you need to read the first 250 bytes of each object in S3. This data contains some metadata about the content of the file itself. Unfortunately, there are over 10,000,000 files in your S3 bucket, and this is about 100 TB of data. The data will then need to be stored in an Aurora Database. How can you build this index in the fastest way possible?
    * Create a program to use a byte range fetch for the first 250 Bytes of data and then store this in the Aurora Database. You cannot query based on byte size in Athena.

1. What EBS Volume type gives you the highest performance in terms of IOPS?
    * EBS Provisioned IOPS SSD (io2 Block Express) is the highest-performance SSD volume designed for business-critical latency-sensitive transactional workloads.

1. You start work for a government agency that is creating a new intranet for internal employees. The department has a sprawl of information across multiple AWS accounts and services, and you need to find a way to make this information searchable. Which AWS service should you consider using?
    * Amazon Kendra. Amazon Kendra allows you to create an intelligent search service powered by machine learning.

### Design Cost-Optimized Architectures

1. You are working in a large healthcare facility which uses EBS volumes on most of the EC2 instances. The CFO has approached you about some cost savings and it has been decided that some of the EC2 instances and EBS volumes would be deleted. What step can be taken to preserve the data on the EBS volumes and keep the data available on short notice?
    * Take point-in-time snapshots of your Amazon EBS volumes. You can back up the data on your Amazon EBS volumes to Amazon S3 by taking point-in-time snapshots. Snapshots are incremental backups, which means that only the blocks on the device that have changed after your most recent snapshot are saved.
