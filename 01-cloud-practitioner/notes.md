# Cloud Practitioner Notes

[Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)

ACG Course - https://learn.acloud.guru/course/aws--certified-cloud-practitioner/overview

## Introduction

Instructor: Keesha Williams
Course orientation: Fundamentals

### Exam Blueprint

* Validates your abilty to explain the value of AWS cloud
* Explain the shared responsibility model
* Security best practices
* Cloud costs and billing practices
* Core services compute network storage database
* Identify core use cases

Recommends 6 months hands on

Exam Content

* Multiple choice
* Multiple response - two or more correct answers out of 5 options
* Most questions scenario based

Domains

* Cloud Concepts - 26%
* Technology - 33%
* Security and Compliance - 25%
* Billing and Pricing - 16%

Minimum Passing Score - 700

### Navigating the Course

Interactive experience, non-linear learning

* View each lesson
* Links in the resources and description sections of the sections

## Foundations of Cloud Coumputing

Cloud computing - delivery of computing services over the internet

* compute
* storage
* networking
* analytics
* development
* security
* databases

Read the [whitepaper](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/aws-overview.pdf)

virtualization - divide the hardware resources on a single pysical server into smaller units

Advantages of Cloud Computing

* Go global in minutes
* Stop spending money running and maintaining data centers
* Benefit from massive economies of scale
* Increase speed and agilty
* Stop guessing capacity
* Trade capital expense for variable expense

Benefits

* High availability - Highly available systems are designed to operate continuously without failure for a long time. These systems avoid loss of service by reducing or managing failures.
* Elasticity - With elasticity, you don't have to plan ahead of time how much capacity you need. You can provision only what you need, and then grow and shrink based on demand
* Agility - The cloud gives you increased agility. All the services you have access to help you innovate faster, giving you speed to market. 
* Durability - Durability is all about long-term data protection. This means your data will remain intact without corruption.

CapEx - upfront purchases toward fixed assets
OpEx - funds used to run day to day operations

Capacity is matched to demand.

Terminology cheet sheet - [here](https://acloudguru.com/blog/engineering/your-aws-terminology-cheat-sheet)

### Cloud Computing Models

* Infrastructure as a Service - fundamental building blocks that can be rented, for exanple a web hosting service
* Complete application, available on demand, offered to users, for example a personal email service
* Platform as a service - used by developers using web-based tools without worrying about underlying infrastructure, for example a storefront website, or aws cloud 9

### Cloud Deployment Models

* Private cloud - company internal data center and network, own your own security, no sharing resources
* Public cloud - get all the benefits of cloud
* Hybrid - combination of private and public, secure sensitive data in on prem data center, supported by DirectConnect

### Leveraging AWS Global Resources

Regions

* A region is a physical location. AWS logically groups regions into geographic locations
* Fully independent and isolated
* Resource and service specific

Availability Zones

* Availability Zones (AZs) consist of one or more physically separated data centers, each with redundant power, networking, and connectivity, housed in separate facilities.
* Characteristics
    * Physically separated
    * Connected through low-latency links
    * Fault tolerant
    * Allows for high availability


Edge Locations

* Cache content for fast delivery to your users
* Latency - Latency is the time that passes between a user request and the resulting response.
* CDN and cloudfront, reduced latency, like a data center but doesn't run your main infrastructure


### Exploring Your Account

* Management console and CLI
* [Materials](https://acloudguru.visme.co/view/jwpjrjyg-s02-l05-exploring-your-amazon-web-services-aws-account)

Root user

* limited use, e.g. delete your account
* always protect via MFA
* root has unrestricted access

Programmatic Access

* CLI
* Appliaction Code
* SDKs

## Technology

Vid - 168 AWS services in 2 minutes

Tech section is 30% of the exam

### Compute


EC2

* elastic compute power
* virtual servers in the cloud

region -> multiple AZs -> multiple data centers -> multiple servers

access your instances via

* AWS management console
* Via SSH (most common way, via a keypair)
* Via EC2 instance connect
* AWS systems manager

Pricing options

* on-demand, billed to the second, can reserve on-demand capacity
* spot - request use of unused capacity, can save up to 90%, pay the spot price in effect at each hour
* reserved instances - commit to a specific instance type in a specific region for a 1 or 3 year term, save up to 75%, must sign a contract, capacity in an AZ, pay partion up front, all up front, per month
    * can use a convertable reserved instance
* dedicated hosts - pay for a physical server dedicated for you exclusive use
    * use for server-bound licences
    * tenancy model demands via regulatory or contractual obligations
* savings plans - commit to compute usage measured by the hour for 1 to 3 years, lower bill across multiple servers, more flexibility, save up to 72% from on demand
    * apply across many compute services - ec2, fargate, lambda

features

* load balancers
* auto scaling

#### Lambda

Write and deploy code without worrying about servers

* Scales automatically
* Focus on core business logic instead of worrying about servers?
* Building block for building serverless apps
    * Serverless means AWS manages the servers for you
* Use cases
    * Real-time file processing
    * Send email notifications triggered by SNS
    * Backend business logic for Alexa

Features

* Supports many popular programming languages
* Author code using your favorite IDE
    * Only responsible for your application code
* Lambda can execute your code in response to events
* 15 minute timeout

Pricing Model

* Based on compute time and request count
* Includes 1 million free requests post free tier usage ("always free option")

#### Addition Compute Services

Fargate - serverless compute engine for containers

* Works with Docker, ECS, EKS
* Scales automatically
* Serverless

Lightsail

* Quickly launch all the resources you need for small projects
* Several preconfigured apps like work press sites
* Simple screens for people with no cloud experience
* includes VMs, SSD storage, data transfer, DNS management, static IP
* Low predictable monthly fee

Outposts

* Run cloud services in your internal data center
* Supports workloads that need to remain on-premises due to latency or data
soverignty needs
* AWS delivers and installs servers in your internal data center
* Used for Hybrid services
* APIs for services you can call on line

AWS Batch

* Allows you to process large workloads in smaller chunks
* Run hundreds and thousands of smaller batch processing jobs
* Dynamically provisions resources based on volume


### Storage Services

#### S3

S3 - object storage service for the cloud that is highly available

* Objects and buckets
* Unlimited storage
* Public or private

Security

* Set security at the bucket or object level using ACLs, Bucket Policies, Access Point policies
* Versioning can be enabled to prevent accidental deletion, preservice prior versions
* Use s3 access logs to track access
* S3 is a regional service with global bucket namespace

Data Accessibility

* Durability - will my data be there tomorrow?
    * 11 nines
* Avaialbilty - can I access my data now?
    * 99.99 

S3 Storage Classes

* Standard
* S3 Intelligent Tiering - good for unknown or changing access patters (new apps), or unpredictable patterns (data lake)
* S3 Standard Infrequent Access (IA) - fast access when you need it
* S3 One Zone Infrequent Access - like IA but one AZ, can lose data 
* S3 Glacier - long term data data storage and archive
    * Data retrieval is longer - tiers are 1-5 minutes, 3-5 hours, 5-12 hours
* S3 Glacier Deep Archive - like glacier but event longer access time (12 hours or 48 hours)
* S3 Outposts - object storage on premises
    * Single storage class, can store data across multiple devices and servers
    * Good for data residency, or if lower latency is needed.

S3 Use Cases

* Static websites with cloudfront for global distribution
* Archive data using glacier
* Store data in s3 for use with analytics services like redshift and athena
* Mobile applications - s3 transfer accelleration for upload to buckets

#### Additional Storage Services

EC2

* Elastic Block Store
    * Storage device that can be attached to and removed from your instance
    * Tied to one AZ, attached a one host in the AX
    * Data persists when instance is not running
    * Recommended for quickly accessible data, running a database on an instance, long-term data storage
* Elastic File System
    * Serverless network filesystem that allows you to share files
    * Can be mounted to multiple (Linux) instances
    * Accessible across multiple AZs in the same region
    * Use cases - main directory for business critical apps, lift and shift of existing enterprise apps
* Instance Store
    * Local storage that is physically attached to the host computer and cannot be removed
    * Temporary/ephemeral - data lost when instance stopped
    * For temporary storage needs, data that is replicated across multiple instances
* Storage Gateway
    * Hybrid storage service, connect on-premises and cloud data
    * Move backups to cloud, low latency access to data, reduce storage
    cost

AWS Backup

* Helps you manage backups across multiple AWS services
* Integrates with resource like EC2, EBS, ECS, and more
* Includes backup plan with both frequency and retention

### Content Delivery Services

CDN - mechanism to deliver content quickly and efficiently based on geographoc location

#### CloudFront

* CDN that provides global distribution of content with low latency
* Make available or restrict based on location
* Speeds up delivery of static and dynamic web content
* Uses edge locations to speed up delivery

Delivery

* If available at the edge, returned directly
* Not presend on the edge, retrieve from origin and cache at edge

Use Cases

* S3 Static Websites
* Prevent DDOS attacks
* IP address blocking

Global accelerator

* Sends your users through the AWS global network when accessing your content, speeding up delivery
* Improves latency and availability of single region applications
* Send traffic through the AWS global network infrastructure
* 60% performance boost
* Automatically reroutes traffic to healthy available regional endpoints

S3 Transfer Acceleration

* Speed up s3 upload and download
* Fast transfer of files over long distancts
* Uses CloudFronts globally distributed edge locations 
* Customers around the work can upload to a central bucket

### Networking Services

#### VPC and Subcomponents

* Networking connects computers together and allows for the sharing of data and applications, around the globe, in a secure manner using virtual routers, firewalls, and network management services.

VPC

* VPC is a foundational service that allows you to create a secure private network in the AWS cloud where you launch your resources.
* Isolate and secure resources
* Spans AZs in a region
* Public and private subnets
    * Private - not accessible from internet
    * Public - NACLs, router and route tables, internet gateway

VPC Peering

* Connect two VPCs together


#### Additional Networking Services

DNS 

* Every computer has an IP address
* DNS translates friendly name to IP address

Route 53

* Highly available, scalable domain name service
* Register domain names
* Performes healthchecks on cloud resources
* Makes Hybrid cloud solutions easier

DirectConnect

* Dedicated physical network connection from your on-premises data center to AWS
* Private connection
* Use cases
    * Large data sets
    * Business critical data
    * Hybrid model

AWS VPN

* Site-to-Site VPN creates a secure connection between your internal networks and your AWS VPCs. 
* Similar to Direct Connect, but data travels over the public internet 
* Data is automatically encrypted
* Connects your on-premises data center to AWS
* Supports a hybrid environment

Site to site VPN architecture

* aws cloud, region, AZs, VPC, private/public subnets, router
* new components
    * virtual private gateway - AWS side
    * customer gateway - customer side

API gateway

* Build and managed APIs
* Integrates with services like lambda
    * Client interacts with gateway, which interacts with lambda and other resources

### Utilizing Databases

* Need a way to collect, store, retrieve, sort, graph, and manipulate data

Types

* Relational
    * RDS - aurora, postgres, mysql, maria db, oracle, SQL server
    * HA and fault tolerance - multiple AZs
    * Aurora
        * 5x faster than normal MySQL and 3x faster than normal PostgreSQL
        * Scales automatically while  providing durability and high availability 
        * 
* NoSQL
    * DynamoDB
        * NoSQL key-value database
        * Fully managed and serverless
        * Scales automatically to massive workloads with fast performance
        * Non-relational
* Graph
    * Amazon Neptune
        * Graph database service
        * Supports highly connected datasets like social media network
* In memory
    * Elasticache
    * Compatible with Redis or Memcached engines
* Document
    * Document DB
        * MongoDB compatible
        * Fully managed and serverless

Scenarios

* Migrate on premises oracle db to cloud - RDS
* Migrate on premises postgres db to the cloud - RDS or Aurora
* Alleviate database load for data that is accessed often - elasticache
* Process large sets of user profiles and socials interaction - neptune
* NoSQL db fase enough to handle millions of requests/second - dynamodb
* Operate mongodb workloads at scale - amazon document db

### Migration and Transfer Services

Database Migration Service

* Migrate on-premises databases to AWS
* Continuous data replication
* Supports homogeneous and heterogeneous migrations

Server Migration Service

* SMS allows you to migrate on-premises servers to AWS.
* Server saved as a new Amazon Machine Image (AMI)
* Use AMI to launch servers as EC2 instances

Snow Family

* Snowcone
    * 8 TB usable storage
    * Offline shipping
    * Online with DataSync
* Snowball and Snowball Edge
    * petabyte scale data transport solution
    * transfer data in and out
    * cheaper than internet
    * edge supports ec2 and lambda
* Snowmobile
    * multi-petabyte or exebyte scale
    * 45 foot shipping container
    * Driven to a data center and loaded into s3
    * High security transport

DataSync

* DataSync allows for online data transfer from on-premises to AWS storage services like S3 or EFS.
* Migrates data from on-premises to AWS
* Copy data between AWS storage services
* Replicate data cross-Region or cross-account  

### Leveraging Analytics Services

Data warehousing

* A data warehouse is a data storage solution that aggregates massive amounts of historical data from disparate sources.
* Data warehouses support querying, reporting, analytics, and business intelligence. They are not used for transaction processing.

Amazon Redshift

* Redshift is a scalable data warehouse solution
* Improves speed and efficiency when querying
* Handles exabyte-scale data

Uses

* When you need to consolidate multiple data sources for reporting
* When you want to run a database that doesn't require real-time transaction processing (insert, update, and delete)

Analytics is the act of querying or processing your data

Athena

* Athena is a query service for Amazon S3.
* Analyze S3 data using SQL
* Pay per query
* Considered serverless

Glue

* Glue prepares your data for analytics.
* Extract, transform, load (ETL) service
* Prepare and load data
* Helps to better understand your data

Kinesis

* Kinesis allows you to analyze data and video streams in real time.
* Analyze real-time, streaming data
* Supports video, audio, application logs, website clickstreams, and IoT

Elastic MapReduce

* EMR helps you process large amounts of data.
* EMR Process big data
* Analyze data using Hadoop
* Works with big data frameworks

Data Pipeline

* Data Pipeline helps you move data between compute and storage services running either on AWS or on-premises.
* Moves data at specific intervals
* Moves data based on conditions
* Sends notifications on success or failure

QuickSight

* QuickSight helps you visualize your data.

### Machine Learning Services

Artificial intelligence (AI) teaches computers to do things that normally require human intelligence. 

Rekognition

* Rekognition allows you to automate your image and video analysis.
* Image and video analysis
* Identify custom labels in images and videos
* Face and text detection in images and videos

Comprehend

* Comprehend is a natural-language processing (NLP) service that finds relationships in text.
* Natural-language processing (NLP) service
* Uncovers insights and relationships
* Analyzes text

Polly

* Polly turns text into speech.
* Mimics natural-sounding human speech
* Several voices across many languages
* Can create a custom voice

SageMaker

* SageMaker helps you build, train, and deploy machine learning models quickly.
* Prepare data for models
* Train and deploy models
* Provides Deep Learning AMIs


Translate

* Translate provides language translation.
* Provides real-time and batch language translation
* Supports many languages
* Translates many content formats


Lex

* Lex helps you build conversational interfaces like chatbots.
* Recognizes speech and understands language
* Build highly engaging chatbots
* Powers Amazon Alexa


### Developer Tools

Cloud 9 

* Cloud9 allows you to write code within an integrated development environment (IDE) from within your web browser.  
* write and debug code
* can preconfigure the dev environment with the needed SDKs and libraries for various scenarios, for example writing lambda functions

CodeCommit

* source control system for private Git repositories
* like gitbub

CodeBuild

* allows you to build and test your application source code
* compile source and run tests
* produces artifacts that are ready to deploy

CodeDeploy

* manages the deployment of code to compute services in the cloud or on-premises
* deploy code to fargate, ec2, lambda, and on premises
* helps maintain app uptime, e.g. rolling deployments

CodePipeline

* automates the software release process
* integrate with code build to build and run tests, with code commit to fetch the source code to build, and code deploy to deploy changes
* ci/cd pipeline

XRay

* helps debug production applications
* map application components
* show flow of end to end requests

CodeStart

* helps developers collaboratively work on development projects
* devs can connect their dev environment to code star
* integrates with code commit, code build, code deploy
* issue tracking dashboard

### Deployment and Infrastructure Management Services

Infrastructure as code

* IaC allows you to write a script to provision AWS resources. The benefit is that you provision resources in a reproducible manner that saves time.

Cloud Formation

* CloudFormation allows you to provision AWS resources using Infrastructure as Code (IaC).
* Provides a repeatable process for provisioning resources
* Create templates for the resources you want to provision

Elastic Beanstalk

* Elastic Beanstalk allows you to deploy your web applications and web services to AWS.
* Orchestration service that provisions resources
* Automatically handles the deployment
* Monitors application health via a health dashboard
* After you upload your Java code, Elastic Beanstalk deploys it and handles capacity provisioning, load balancing, and Auto Scaling. Elastic Beanstalk even monitors the health of your application. 

Ops Works

* OpsWorks allows you to use Chef or Puppet to automate the configuration of your servers and deploy code.
* Manage on-premises servers or EC2 instances in AWS Cloud
* Chef and Puppet both supported

### Utilizing Messaging and Integration Services

* Coupling defines the interdependencies or connections between components of a system. Loose coupling helps reduce the risk of cascading failures between components.

Simple Queue Service

* SQS is a message queuing service that allows you to build loosely coupled systems.
* Allows component-to-component communication using messages 
* Multiple components (or producers) can add messages to the queue
* Messages are processed in an asynchronous manner

The are often times that users of your applications need to be notified when something happens

Simple Notification Service - SNS

* Send (plain) emails and text messages
* Publish messages to a topic
* Subscribe to a topic and recieve messages

SES - Simple EMail Services

* Send richly formatted emails from your application
* Good for marketing campaigns and professional emails
 * Send marketing emails and track open rates

### Auditing, Monitoring, Logging

These services give you insight into how well your systems are performing and help you proactively find and resolve errors.

Answer questions like:

* Who signed in and made changes via the AWS Management Console?
* What is the current load on this EC2 instance? 
* What is the root cause of this application error?
* Which execution path resulted in this error? 


CloudWatch

* CloudWatch is a collection of services that help you monitor and observe your cloud resources
* Collects metrics, logs, and events
* Detect anomalies in your environment
* Set alarms
* Visualize logs

CloudWatch is a collection of services

* CloudWatch Alarms
* CloudWatch Logs
* CloudWatch Metrics
* CloudWatch Events

Typical uses

* Real time monitoring on EC2 instances
* Recieve a notification when root user activity is observed in your system
* Billing alarms


CloudTrail

* CloudTrail tracks user activity and API calls within your account
* Log and retain account activity 
* Track activity through the console, SDKs, and CLI
* Identify which user made changes
* Detect unusual activity in your account

You can troubleshoot events over the past 90 days using the CloudTrail event history log to find the specific time an event occurred on a per-Region basis. You can create a custom trail to extend past 90 days.

Things you can track

* Username
* Event time and name 
* IP address
* Access key id
* Region
* Error code

### Exploring Additional Services

Workspaces

* Host virtual desktops in the cloud 
* Windows and Linux
* Enable employees to work from home

Amazon Connect

* Build contact center or help desk in the cloud
* Provide customer service functionaliyt
* Improves productivity of desk agents

## Security and Compliance

### Shared Responsibility Model

Shared security responsibility

* AWS - security of the cloud
    * Hardware, software, networking, facilities, etc.
    * Managed services
* Customer - security in the cloud
    * Application data, encryption options
    * Security configuration
    * Patching - guest OS
    * Identity and access management
    * Network traffic, firewall config
    * Installed software

EC2 Mode

* CUstomer
    * Installed apps
    * PAtching guest OS
    * Security controls
* AWS
    * EC2 service
    * Patching the host
    * Security of the physical server


Lambda 

* Customer
    * Security of the code
    * Storage of sensitive data
    * IAM for permissions
* AWS
    * Lambda service
    * Upgrading lambda languages
    * Lambda endpoints
    * Operating system
    * Underlying infrastructure
    * Software dependencies

Shared

* Patch management
* Configuration management
* Awareness and training

Security breach?

* Rotate all passwords and access keys
* Contact aws trust and safety team

### Well Architected Framework

6 pillars

* Operational excellence
* Security
* Reliability
* Performance efficiency
* Cost optimization
* Sustainability

### IAM

What can only the root user do?

Close your account
Change email address 
Modify your support plan


What can individual users do?

Launch EC2 instances
Configure databases]
Perform administrative tasks 
Access application code

### Application Security Services

WAF - web application firewall

* Blocks attack patterns
* Protects against SQL injection
* Protects against cross site scripting
* Protect cloudfront, application load balancers / EC2 web servers

DDOS

* Crash a web app via overloading it with traffic
* AWS Shield is a managed DDOS protection service - standard is free, advanced is free
* Advanced
    * Enhanced protections
    * 24x7 access to AWS exports
    * Available on cloud front, route 53, ELB, AWS global accelerator
* Real time notifications, support during incidents (advanced)


Macie

* Discover sensitive data on s3 data via ML
* passport numbers, SSN, credit cards, etc.


### Additional Security Services

AWS Config

* Set guard rails
* Set and audit settings on services in your account
* Track config changes over time, stores in s3
* Notifications on config changes

AWS Guard Duty

* Intelligent threat detection system, malicious or unauthorized activity
* ML based
* Built in detection for EC2, S3, IAM
* Reviews cloud trail, vpc flow logs, dns logs
* Anamoly detection - API calls
* Alerts or take action via automation

AWS Inspector

* WOrks with EC2 instances to uncover and report vulernabilities
* Reports on found vulnerabilities
* checks remote access, root access, etc
* Build in rules
* Agent installed on ec2 instances

AWS Artifact

* On demand access to AWS security and compliance reports
* Central repo for third party auditors

AWS Cognito

* Secure access to web apps and mobile apps
* AuthN and AuthZ 
* Manage users
* Built in tools to sign up, sign in
* Federation with social media accounts

### Data Encryption and Secrets Management Services

* Data in flight, data at rest
* Encryption as a data protection mechanism

KMS

* Key management service
    * Generate, store, manage keys
    * Aws manages the keys

CloudHSM

* cloud hardware security module used to generate encryption keys
* meet security requirements that require dedicated hardware
* customer manages the keys

Secrets Manager

* Manage and retrieve secrets, e.g. database credentials
* Rotate, manage, and retrieve secrets
* Encrypt secrets at rest

## Pricing, Billing, Governance

Cost drivers

* Compute
* Storage
* Outbound data transfer

Whitepaper: How AWS Pricing Works

Free offers

* 12 months free following AWS sign up, subject to usage
* Always free
* Trials - free starting from service activation

EC2 pricing

* on demands
* savings plan - commit to usage
* reserved usage
* spot instances
* dedicated hosts

Lambda pricing

* Based on number of requests, includes start/stop time interval, first 1 million free


S3

* Pay for storage
* Price based on location, storage class
* Data transfer out of s3 region
* Requests and data retrieval


RDS

* Running clock hours
* Type of database 0 engine, size, memory class
* Purchase type - on demand, reserved
* Number of instances
* API calls
* Deployment type - 1 or multiple AZs
* Outbound data transfer

TCO - financial estimate to understand direct and indirect costs

* Calculator no longer available

Application Discovery Service

* Tools to help plan migrations to AWS
* Used to estimate TCO
* Works with other services to migrate servers

Ways to minimize TCO using AWS

* Minimize capital expenditures
* Utilize reserved instances
* Right size your resources

Pricing calculator - use to estimate TCO

AWS Price List API

* call to get prices
* get notifications of price changes

### Billing Services

Budgets

* Allow you to set custom budgets to alert you when when your costs or usage exceed your budgeted amount
* Improve planning and cost control
* Cost, usage, and reservation budget
    * Cost - how much to spend on a service
    * Usage - plan how much to use on a service
    * Reservation budgets - Set RIs or savings plans utilization or coverage targets
* Budget alerts - email, SNS, chat (chime, slack)

Can monitor free tier usage

Cost and Usage Report

* Most comprehensive set of cost and usage data
* Downloadable report
* Aggregate usage on different time dimensions


Cost Explorer

* Visualize your cost over time
* Can forcast

Cost Allocation Tags

* Label resources using key and value pair
* Tags allow you to track costs via cost allocation report


### Governance Services

Maintain control of cost, compliance, security across all your AWS accounts

Organizations

* Centrally manage multiple accounts under one umbrella
* Group multiple accounts
* Single paymenet for all accounts
* Automate account creation
* Allocate resources and manage access policies across all groups

Master payer account

Organization service control policies - policies all must follow

Organizational Units
Member Accounts

Organization benefits

* Consolidate billing
* Cost savings - e.g. volume discounts from combined usage
    * Save money with reserved instance sharing
* Account governance

Control Tower

* Sits on top of organizations, helps ensure accounts conform to company policies
* Works directly with organizations
* Enforces the best use of services across accounts
* Provides a dashboard to help manage accounts

Systems Manager

* Visibility and controls over AWS resources
* AUtomate operational tasks on your resources
* Group resources and take action
* Patch and run commands on multiple EC2 and RDS instances

Trusted Advisor

* Provides real time guidance to help you provision your resources according to AWS best practices
* CHecks your account and makes recommendations
* Check service limits 
* Makes recommendations
* Free checks, upgraded checks based on support subscription

License Manager

* Helps you manage software licenses
* On prem and AWS licences
* ORacle, Microsoft, SAP, more

Certificate Manager

* Provides public and private certificates for free
* Integrates with ELB, API GW, and more


