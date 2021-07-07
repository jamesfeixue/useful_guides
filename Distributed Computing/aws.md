# AWS Developer: Building on AWS

[Course Syllabus](https://courses.edx.org/assets/courseware/v1/726ccfc9b59e4c45212ef2dfa1d136b8/asset-v1:AWS+OTP-AWSD1+2T2019+type@asset+block/Building_on_AWS_Syllabus.pdf)

1. Which compute services?
2. Storage and database services?
3. Security and authentication?
4. User requests?
5. Integrate pieces of application using messaging queues and notifications. 


### Getting Started
Project: web service where users can sign-up, upload photos, and print photos
- standard requirements: user registration, secure user directory, email verification, password requirements, password resets, etc
- photo storage: image files, structured data for description, and computer vision generated labels (API)
- communicating upload event to trigger on-premise processing and printing
- troubleshoot performance issues, telemetry data to build map of services used by application, determine latency and identify errors

## Basics
- Intro to **EC2 (Elastic Compute Cloud)**
  - APIs
  - scalability/re-sizable compute capacity
  - failure resilient  
  - virtual instance for Linux
  - metadata security
  - networking features
  - remote admin with SSH

- Launching EC2
  - configure **amazon machine image (AMI)**
  - instance type / hardware profile
  - security groups
  - storage
  - key pairs

## Cloud Infrastructure and Responsibility

### Virtual Server Infrastructure

- Basics
  - virtual machine provide VCPU and RAM resources
  - runs on a host server and a **hypervisor** mediates access between code and server
  - hypervisor also provides isolation from other workloads
  - **availability zone (AZ)** is a logical grouping of data centers where the host is located e.g. us-west-2b
  - also offer DNS, CDN (content delivery network) to cache web content a.k.a. infrastructure edge locations
  - Service Oriented Architectures and APIs in AWS

- Availability Zones
  - each AZ within a region is isolated from other for catastrophe prevention
  - each region e.g. us-west-2 has multiple AZs  

- Scope
  - each region has its own API endpoint
  - some services require specific AZ be selected (EC2) and resources are bound to that AZ
  -  S3 will be regional in scope and data will be replicated within AWS facilities within a region
  -  Identity and Access Management are noot limited to a region e.g. users can make api calls not bound to particular geographic region
  
### Amazon Virtual Private Cloud (VPC)
- An isolated network
  - private ip address
  - optional public ip address, also Elastic IP
  - can be connected to corporate networks, private networks
  - scope: regional

- IP address (internet protocol)
  - IPv4 defiines an IP address as a 32-bit number
 
- **subnets**: because managing IP addresses on a per-instance basis is hard
  - subnet given a range of IP addresses using **CIDR notation**, which is a representation of an ip address e.g. 10.0.0.0/16
  - /16 refers to keeping the first 16 bits fixed
  - VPC has an overall CIDR block
  - scope: AZ
  - Use CloudFormation template to manage the subnets in a VPC

- network traffic between subnets
  - traffic between subnets is enabled by default
  - need internet gateway (connection type for VPC) for webservers to have direct access to internet
  - rules that route traffic from web server subnet out to internal gateway in route tables
  - do not associate such rules for subnets we want to keep private

### Developer responsibility



### EC2 Metadata
### Logs, SSH, instance metadata

## Invoking AWS APIs & AWS Identity and Access Management

## Amazon S3

## Working with Development Environment

## Amazon Rekognition

## Storing Structured Data using AWS Managed Databases

## Availability and Application Failure

## Adding Support for Users and Private Data to the Application

## Debugging and Profiling a Distributed System

## Taking a Task Off the Server Asynchronously

## Making System More Distributed

## Queueing and On-Premise Hardware

