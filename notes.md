# Notes

- [Notes](#notes)
  - [High Level Notes](#high-level-notes)
    - [AWS Training Page](#aws-training-page)
    - [AWS Exam Guide](#aws-exam-guide)
    - [AWS Sample Questions](#aws-sample-questions)
  - [EC2](#ec2)
    - [Linux User Guide](#linux-user-guide)
  - [Terminology](#terminology)

## High Level Notes

### AWS Training Page
[Web Link](https://aws.amazon.com/certification/certified-solutions-architect-associate/)

* Recommended knowledge
  * Experience w/ AWS compute, networking, storage and DB services
  * Experience w/ AWS deployment and management services
  * Identify the technical requirements and needs of a project
  * Identify which services meet the technical requirements
  * Recommneded best practices for secure and realiabe apps
  * Basic AWS architecture principles
  * AWS global infrastructure
  * AWS network technologies
  * AWS security features and tools along with their traditional counterparts
* Exam setup
  * Cost = $150
  * Time = 130 minutes
  * Multiple choice
* Suggestions
  * Focus on whitepapers
  * Use the exam guide and sample questions

### AWS Exam Guide
[Guide Doc](high_level/AWS-Certified-Solutions-Architect-Associate_Exam-Guide.pdf)

* Response types
  * Multiple choice: single correct response and 3 incorrect
  * Multiple response: two correct responses out of 5 total
* Unanswered questions are marked as incorrect
* Pass/fail based on a minimum standard established by AWS professionals
  * Reported from 100 to 1,000 with a minimum passing score of 720
* Scoring also contains the performance as a whole and on each section level
* Domains
  * 1 - Design Resilient Architectures
    * Design a multi-tier architecture solution
    * Design highly available and/or fault tolerant architectures
    * Design decoupling mechanisms using AWS services
    * Choose appropriate resilient storage
  * 2 - Design High-Performing Architectures
    * Identify elastics and scalable compute solutions for a workload
    * Select high-preforming and scalable storage solutions for a workload
    * Select hig-performing networking solutions for a workload
    * Choose high-performing database solutions for a workload
  * 3 - Design Secure Applications and Architectures
    * Design secure access to AWS resources
    * Design secure application tiers
    * Select appropriate data security options
  * 4 - Design Cost-Optimized Architectures
    * Identify cost-effective storage solutions
    * Identify cost-effective compute and database services
    * Design cost-optimized network architectures

### AWS Sample Questions
[Sample Doc](high_level/AWS-Certified-Solutions-Architect-Associate_Sample-Questions.pdf)

1. A CRM application runs in EC2 in multiple AZ's behind an Application Load Balancer. If one fails, what occurs?
   1. The load balancer will stop sending requests to the failed instance - A
   2. ALB's send health checks ot instances and only sends requests to healthy instances, it does not restart the instance

## EC2

### Linux User Guide
[User Guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)

* What is Amazon EC2?
  * Elastic Compute Cloud provides scalable computing capacity
  * No hardware investment
  * Features of EC2
    * Virtual compute environments, known as instances
    * Preconfigured templates, known as Amazon Machine Images (AMIs), including OS and software
    * Secure login with key pairs
    * Temporary storage volumes, known as instance store volumes
    * Persistent storage volumes using Elastic Block Store (EBS)
    * Multiple physical locations, including regions and availability zones
    * Firewall and security groups
    * Static IPv4 addresses, known as elastic IP addresses
    * Metadata, known as tags
    * Virtual networks isolated fro the rest of AWS, known as Virtual Private Clouds (VPC)
  * Instances and AMIs
    * AMIs (Amazon Machine Instances) are templates that contain the OS and other software like servers
    * AMIs are used to launch instances across multiple machines
    * Instances are virtual servers
    * Instance types define the resources of the host (RAM, vCPUs, etc.) and multiple instance types can be launched from the same AMI
    * [Instance Types](https://aws.amazon.com/ec2/instance-types/) as of 11/05/20
    * AWS accounts have limits on the number of live instances, see [here](http://aws.amazon.com/ec2/faqs/#how-many-instances-ec2)
    * Storage blocks are allocated upon launch but are deleted upon failure, hibernation, or termination
    * Security Best Practices
      * Use AWS IAM (Identity and Access Management)
      * Restrict access by allowing only trusted hosts or networks to access ports
      * Review the rules inside security groups and ensure the principle of least privilege (only open permissions based on requirements)
      * Consider a bastion security group that allows external logins and the rest inside a more secure group
      * Disable password based logins for instances, especially root
    * Stopping an instance performs a normal shutdown and retains the EBS attached volumes
    * Costs are not accrued while stopped, but each stop operation is charged at least one minute
    * Terminating instances deletes the root volumes and the instance, while retaining the EBS volumes
    * Termination can be disabled by instance
  * Regions and Zones
    * Regions are separate geographic areas
    * Availability Zones are multiple, isolated locations within a region
    * Local zones provide placement of resources closer to the end users
    * Outposts bring AWS services and infrastructure to other data centers, co-location space, or on-prem facilities
    * Wavelength zones allow deployment to low latency 5G devices and end users in edge locations on telecom carriers' networks\
    * Viewing resources only shows those that are available in the region you are working in and automatic replication is not the norm
    * There are costs for data transfer between regions
    * [Global infrastructure](https://aws.amazon.com/about-aws/global-infrastructure/)
    * Availability zones allow for you to select where to deploy resources or AWS can automate selection
    * Elastic IPs can be used to mask failure in a single AZ by mapping to another AZ
    * Outposts are AWS managed resources on-prem or in user defined locations and must be ordered based on the Outpost [catalog](http://aws.amazon.com/outposts/pricing/)
  * Root Device Volumes
    * You can choose to launch instances with EBS or instance stores
    * EBS is recommended as they launch faster and use persistent storage
    * EBS volumes allow for restarting instances without losing data, although the default is to delete when the instance is terminated
* Best Practices
  * Security
    * Manage instances using federation, IAM users and IAM roles
    * Establish credential management policies and procedures
    * Implement least permissive rules for security groups
    * Regularly patch and update OS and applications
  * Storage
    * Understand the root device types
    * Use separate EBS volumes for the OS and the data, ensuring that data persists after instance termination
    * Use instance stores to store temporary data
    * Encrypt EBS volumes and snapshots
  * Resource Management
    * Use instance metadata and custom resource taags to track and identify resources
    * View and request resource limits in advance
  * Backup and Recovery
    * Regularly backup EBS volumes using snapshots
    * Deploy critical components accross AZs and replicate appropriately
    * Design applications to handle dynamic IPs
    * Monitor and respond to [events](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/monitoring_ec2.html)
    * Ensure you are ready for failover
      * You can use elastic network interfaces to replacement instances
      * You can also use EC2 Auto Scaling
    * Regularly test the recovery and failure process
  * Networking
    * Set the TTL (Time to Live) values to 255 for IPv4 or IPv6
* Amazon Machine Instances
  * Includes
    * One or more EBS snapshots or root templates
    * Launch permissions that control access
    * Block device mapping for volume attachment
  * AMI Types
    * Can be selected based on region, OS, architecture, launch permissions and root storage
    * Launch permissions
      * Public = owner grants permissions to all AWS accounts
      * explicit = owner grants access to certain accounts
      * implicit = the owner has implicit permissions
    * Developers can charge for their images per guidelines
    * Root device storage
      * EBS usually takes less than a minute to boot, sized up to 16 TiB, is deleted upon termination (but that can be altered), types can be altered and storage and snapshots are charged
      * Instance stores usually launch in under 5 minutes, 10GiB sized disks, is only persisted during instance life, type alterations are not available and only S3 for AMI storage is charged
  * Virtualization Types
    * PV = paravirtual
    * HVM = hardware virtual machine
    * Best performance can be found with current gen types and HVMs
    * HVM
      * Presents a fully virtualized set of hardware
      * Allows an OS to run directly without modifications
      * Can access hardware extensions like GPUs and networking
    * PV
      * Boot with PV-GRUB which starts the boot cycle then chain loads the kernel
      * Can be run on hardware without explicit support
      * Cannot access hardware extenstions
      * Not all AZ or Regions support this type
  * Shared AMIs
    * Guidelines
      * Update AMI tools
      * Disable password based remote logins
      * Disable local root access
      * Remove SSH host key pairs
      * Install public key creds
      * Disable sshd DNS
  * Paid AMIs
    * AWS Marketplace allows you to buy software for AWS including AMIs
    * Pricing and charges are set by the owner and charged on top of normal fees
  * Spot instances are only run on demand and on different hosts
  * Reserved instances are purchased for a period and reserves a host
  * Amazon Linux
    * Provided by AWS
    * Designed for stability, security and high performance
    * Includes packages for AWS integration
    * AWS provides ongoing security and maintenance
    * Most applications designed to run on CentOS run on Amazon Linux
    * Amazon Linux 2 is also bundled with the MATE desktop
* Instances
  * Before launching
    * What type best suits my needs?
    * What purchasing option suits my needs?
    * What root volume suits my needs?
    * Can I remotely manage a fleet of instances in my hybrid environment?
  * Instance Types
    * [All types](http://aws.amazon.com/ec2/instance-types/)
    * General Purpose
      * A1
        * Scale-out suited and supported by ARM
        * Usually web servers and containerized microservices
      * M5 and M5a
        * Balanced use
        * Small and midsize DBs
        * Memory processing
        * Caching fleets
        * Backend servers for SAP, SharePoint and cluster applications
        * Metal instances provide direct hardware access
      * M6g and M6gd
        * Powered by Graviton2 processors
        * App servers
        * Microservices
        * Gaming servers
        * Midsize data stores
        * Caching fleets
      * T2, T3, T3a and T4g
        * Baseline CPU with high burst performance
        * Websites and web apps
        * Code repos
        * Development, build, test and staging environments
        * Microservices
      * Networking ranges from 1 Gbps to 100Gbps
    * Compute Optimized
      * C5 and C5n
        * Batch processing
        * Media transcode
        * High-perf web servers
        *  HPC = High Performing Compute
        *  Scientific modeling
        *  Game servers
        *  ML inference
     *  C6g and C6gd
        *  Same as above but also CPU inference and distributed analytics
    *  Memory optimized
       *  R5, R5a and R5n
          *  High performance relationa; (MySQL) and NoSQL (MongoDB, Cassandra) DBs
          *  Distributed web scale cache stores with key-value memory caching (Memcached and Redis)
          *  In-mem DBs like SAP HANA
          *  Real time big data processing like Hadoop and Spark
          *  HPC and Electronic Design Automation
       *  R6 and R6gd
          *  Open source DBs (MySQL, MariaDB and PostgresSQL)
          *  In-mem caches
       *  High memory
          *  Up to 24 TiB per instance
          *  Optimized for in-mem DBs like SAP HANA
       *  X1
          *  In-mem DBs
          *  Big data processing
          *  HPC
       *  X1e
          *  High performance DBs
          *  In-mem DBs
       *  z1d
          *  Electronic Design Automation
          *  Relational DBs
    *  Storage optimized
       *  D2
          *  Massive parallel processing (MPP) data warehouse
          *  MapReduce and Hadoop
          *  Logs or data processing
       *  H1
          *  MapReduce and HDFS
          *  Sequential, large volume access to direct attached storage
          *  High throughput
       *  I3 and I3en
          *  High frequency OLTP 
          *  Relational DB
          *  NoSQL DB
          *  Cache for in-mem DB
          *  Data warehousing
          *  HDFS
    *  Accelerated computing
       *  Uses hardware accelerators like GPUs and co-processors
       *  GPU instances
          *  G4
             *  Tesla GPUs
             *  Best for CUDA and ML
             *  16GB per GPU
          *  G3
             *  Tesla M60 GPUs
             *  Best for virtualized desktops, GRID applications, 3D rendering
          *  G2
             *  Grid K520 GPUs
             *  Video creation
          *  P4
             *  A100
             *  ML and HPC
             *  400gbps
             *  Elastic Fabric Adapter (EFA)
          *  P3
             *  V100
             *  General purpose and deep learning
             *  32GB of memory
          *  P2
             *  K80
       *  AWS Inferentia instances
          *  Designed to accelerate machine learning with high performance and low latency inference
          *  Specifically designed for deep learning inference
          *  Multiple ways to access:
             *  SageMaker
             *  Inf1 with Deep Learning AMI
             *  Inf1 instance with Neuron SDK
             *  Container using Inf1 instance and ECS optimized AMI
             *  EKS cluster with Inf1 instances
          *  Inf1
             *  Inferentia custom designed chip
       *  FPGA instances
          *  Accelerate things like genomics, financial analysis, video processing and security
          *  F1
             *  Xilinx UltraScale+ VU9P FPGAs
             *  2.5 million logic units
             *  6800 Digital Signal Processors (DSP)
             *  64GB of ECC RAM
       *  NVIDIA drivers
          *  Main types:
             *  Tesla
             *  GRID
             *  Gaming
          *  Can be installed by using an AMI or by installing public drivers
       *  You can also install other variant of CUDA
  *  Recommendations
     *  Compute Optimizer offers instance recommendations based on performance, money or a mixture
     *  Generally only considers M, C, R, T and X types
     *  Will classify an instance as:
        *  Under-provisioned
        *  Over-provisioned
        *  Optimized
        *  None
*  Monitoring
   *  

## Terminology
* EC2 = Elastic Compute Cloud
* AMI = Amazon Machine Image
* EBS = Elastic Block Storage
* VPC = Virtual Private Cloud
* IAM = Identity and Access Management
* AZ = Availability Zone
* TTL = Time To Live
* PV = paravirtual
* HVM = hardware virtual machine
* DB = database
* HPC = High Performing Compute
* EFA = Elastic Fabric Adapter
* EKS = Elastic Kubernetes Service
