# Presentation
# ☁️ AWS Mini-Presentation: EC2, AMI, EBS & Load Balancing

This document provides a quick and clear overview of four essential AWS services used to deploy, store, and scale applications in the cloud.

---

## 1. 🖥️ EC2 (Elastic Compute Cloud)

**EC2** is Amazon’s IaaS offering that allows you to rent virtual machines to run applications.

### 🔹 Key Features:
- Scalable compute power in the cloud
- Supports a variety of **instance types** (optimized for memory, CPU, etc.)
- Fully configurable: OS, storage, networking, permissions
- Integrates with **key pairs**, **security groups**, **IAM roles**, and **EBS volumes**

### 🧪 CLI Example:
```bash
aws ec2 run-instances \
  --image-id ami-0abcdef1234567890 \
  --count 1 \
  --instance-type t2.micro \
  --key-name MyKeyPair \
  --security-groups MySecurityGroup
✅ Use Case:
Spin up a web server, application server, or test environment in minutes.

2. 🧱 Amazon Machine Image (AMI)
An Amazon Machine Image (AMI) is a pre-configured template that contains the operating system, application server, and installed applications used to launch EC2 instances.

🔹 Key Points:
AMI = Snapshot of a configured EC2 instance

Used to quickly launch new EC2 instances with identical setup

Includes:

Operating System (e.g., Amazon Linux, Ubuntu)

Pre-installed software (e.g., web servers, security tools)

Custom files and configurations

✅ Example Use Case:
After installing Apache, PHP, and MySQL on an EC2 instance, create a custom AMI so future servers are ready in minutes.

3. 💾 EBS (Elastic Block Store)
EBS is persistent block storage for EC2 instances—like a virtual hard drive.

🔹 Key Features:
Persistent: Data remains intact after instance stop/restart

Can be attached/detached from EC2 instances

Supports backups via snapshots, which can also be used to create AMIs

Configurable for performance (e.g., general purpose SSD, provisioned IOPS)

✅ Example Use Case:
Store application logs or databases on an EBS volume, back it up regularly using snapshots, and restore as needed.

4. ⚖️ Load Balancing (ELB)
Elastic Load Balancing (ELB) automatically distributes incoming application traffic across multiple EC2 instances.

🔹 Types of Load Balancers:
Application Load Balancer (ALB) – Layer 7 (HTTP/HTTPS), supports path-based routing

Network Load Balancer (NLB) – Layer 4 (TCP/UDP), optimized for high performance

Gateway Load Balancer – Used for integrating third-party virtual appliances (e.g., firewalls)

🔹 Benefits:
Ensures high availability and fault tolerance

Helps in auto-scaling and traffic distribution

Can handle SSL termination and manage sessions

🧩 Basic Architecture:
less
Copy
Edit
          [ Internet Users ]
                  |
        [ Elastic Load Balancer ]
              /            \
       [ EC2 Instance ]  [ EC2 Instance ]
✅ Example Use Case:
Deploy a web application behind an ALB that routes traffic to healthy EC2 instances across multiple Availability Zones.