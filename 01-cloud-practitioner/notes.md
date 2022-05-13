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
