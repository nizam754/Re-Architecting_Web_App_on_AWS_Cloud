# Re-Architecting Web App on AWS Cloud [Cloud Native]

## About the Project
- Multi Tier Web Application Stack.
- Re-Architect Services for AWS Cloud.
- Architecture to boost agility or improve business continuity.

## Scenario
- Project services running on Physical/Virtual/Cloud machines.
- Varieties of services that powers your project runtime.
- Need time for the teams 
    - Cloud Computing Team
    - Virtualization Team
    - DC Ops Team
    - Monitoring Team
    - Sys Admin etc involved.

## Problem
- Operational Overhead
- Struggling with Uptime & Scaling 
- Upfront CapEx & Regular OpEx
- Manual Process / Difficult to automation

## Solution
- Cloud Setup
  - Automation
  - IAAC
  - PayAsYouGo
  - PAAS & SAAS
  - Flexibility

## AWS Services
- Beanstalk (VM for Tomcat - app server)
- Beanstalk (NGINX LB Replacement)
- Beanstalk (Automation for VM Scaling)
- S3/EFS (Storage)
- RDS Instance (Databases)
- Elastic Cache (Memcached)
- Route53 (DNS)
- Cloudfront (Content Delivery Network)

## Objective
- Flexible Infrastructure
- No Upfront Cost
- IAAC
- PAAS
- SAAS

## Comparison
| Beanstalk | Tomcat Ec2/VM |
| --- | --- |
| ELB in Beanstalk | Nginx LB/ELB |
| Autoscaling | None/Autoscaling |
| EFS/S3 | NFS/S3/EFS |
| RDS | MySQL On VM/Ec2 |
| Elastic Cache | Memcached on VM/Ec2 |
| Active MQ | RabbitMQ On VM/Ec2 |
| Route53 | Namecheap, Local DNS |
| Cloudfront | None/Multi DC across world |

## Architecture of AWS services for the project
- EC2 Instances
- ELB
- Autoscaling
- EFS/S3
- RDS
- Elastic Cache
- Active MQ
- Route53
- Cloudfront

![Architecture1!](images/Architecture1.png)

## Flow of Execution
1. Login to AWS Account
2. Create Key Pair for beanstalk instance login
3. Create Security group for Elastic cache, RDS & ActiveMQ
4. Create
   - RDS
   - Amazon Elastic Cache
   - Amazon Active MQ 
5. Create Elastic Beanstalk Environment
6. Update SG of backend to allow traffic from Bean SG
7. Update SG of backend to allow internal traffic
8. Launch Ec2 Instance for DB Initialing
9. Login to the instance and initialize RDS DB
10. Change healthcheck on beanstalk to login
11. Add 443 https Listner to ELB
12. Build Artifact with backend information
13. Deploy Artifact to beanstalk
14. Create CDN with SSL certificate
15. Update entry in NameCheap DNS Zones.
16. Test the url.