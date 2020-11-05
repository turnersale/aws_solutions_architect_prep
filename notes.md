# Notes

- [Notes](#notes)
  - [High Level Notes](#high-level-notes)
    - [AWS Training Page](#aws-training-page)
    - [AWS Exam Guide](#aws-exam-guide)
    - [AWS Sample Questions](#aws-sample-questions)
  - [EC2](#ec2)
    - [Linux User Guide](#linux-user-guide)

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
  * 
