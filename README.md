## 🧱 AWS VPC 

Amazon Virtual Private Cloud (VPC) allows you to provision a logically isolated section of the AWS cloud where you can launch AWS resources in a virtual network. Vpc provide secure, scalable, and highly available network architectures in AWS—comparable to traditional hardware infrastructure but more flexible and programmable.

The following diagram shows an example VPC. The VPC has one subnet in each of the Availability Zones in the Region, EC2 instances in each subnet, and an internet gateway to allow communication between the resources in your VPC and the internet.
![AWS VPC Diagram](how-it-works.png)

---

### 1. 🌐 **Subnets** – Sub-networks inside your VPC

Subnets divide your VPC’s IP address range into smaller chunks. Each subnet can be either public, private, or isolated, depending on the intended level of internet access.

- **Public Subnet**: Connected to the internet via an Internet Gateway. Use for resources like web servers or load balancers.
- **Private Subnet**: Has no direct internet access. Use for internal resources like databases or backend services.
- **Isolated Subnet**: Completely cut off from the internet (no IGW or NAT). Useful for high-security workloads.

📘 *Example:*  
If your VPC has a CIDR block `10.0.0.0/16`, you might create:
- `10.0.1.0/24` as a public subnet
- `10.0.2.0/24` as a private subnet

---

### 2. 🗺️ **Route Tables** – Directing network traffic

Route tables define how network traffic is routed within your VPC. Every subnet must be associated with a route table, and that table determines where traffic goes.

- Each route consists of a **destination** (CIDR block) and a **target** (like an Internet Gateway, NAT Gateway, or local).
- Public subnets typically have a route to the Internet Gateway (`0.0.0.0/0 → igw-xxxxxx`).
- Private subnets often route traffic through a NAT Gateway.


---

### 3. 🌍 **Internet Gateway (IGW) / NAT Gateway** – Internet access control

These are gateways that control **internet connectivity** for your VPC.

- **Internet Gateway (IGW):** Lets resources in public subnets send and receive traffic from the internet.
- **NAT Gateway (NGW):** Allows resources in private subnets to **initiate outbound** internet traffic (e.g., for software updates) **without receiving inbound** traffic.

📘 *Use case:*  
- Public-facing EC2 instance (web server): attach to public subnet + IGW  
- Database in private subnet: update software via NGW, but block inbound internet access

---

### 4. 🔐 **Security Groups & Network ACLs** – Firewalls for your VPC

AWS provides two main types of firewalls:

- **Security Groups (SG):**
  - Operate at the **instance level**
  - **Stateful**: if you allow inbound, the response is automatically allowed
  - Example rule: Allow port 80 (HTTP) from anywhere

- **Network ACLs (NACLs):**
  - Operate at the **subnet level**
  - **Stateless**: you must define both inbound and outbound rules
  - Useful for blocking specific IP ranges or controlling low-level traffic


---

### 5. 🔄 **VPC Peering / VPN / Direct Connect** – Connecting your VPC to other networks

AWS provides multiple ways to connect your VPC to other networks:

- **VPC Peering**:
  - Connects two VPCs privately across AWS
  - Traffic uses AWS internal backbone (not public internet)
  - Good for communication between microservices across VPCs

- **VPN Gateway**:
  - Establishes an encrypted tunnel between your **on-premises network** and AWS
  - Useful for hybrid cloud setups

- **Direct Connect**:
  - Provides a **dedicated fiber connection** between your data center and AWS
  - Offers lower latency, more consistent network performance than VPN


---


