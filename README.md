## 🧱 AWS VPC 

A Virtual Private Cloud (VPC) is a logically isolated network in AWS, similar to a traditional data center. Here are the 5 most essential components ("slices") that make up a typical VPC:

---

### 1. **Subnets**
- Sub-divide your VPC's IP range into smaller networks
- Types:
  - **Public Subnet**: Can access the internet (via IGW)
  - **Private Subnet**: No direct internet access
  - **Isolated Subnet**: No inbound/outbound internet access
- Example:  
  `10.0.1.0/24` for public resources  
  `10.0.2.0/24` for private resources

---

### 2. **Route Tables**
- Define how traffic is directed within the VPC
- Each subnet must be associated with one route table
- Routes examples:
  - `0.0.0.0/0 → igw-xxxxxxxx` (Internet Gateway)
  - `10.0.2.0/24 → local` (Internal routing)

---

### 3. **Internet Gateway / NAT Gateway**
- **Internet Gateway (IGW)**: Allows public subnets to access the internet
- **NAT Gateway**: Enables outbound internet access from private subnets
- IGW is attached to the VPC; NAT is placed in a public subnet

---

### 4. **Security Groups & Network ACLs**
- **Security Groups**: Act as virtual firewalls at the instance level (stateful)
- **NACLs (Network Access Control Lists)**: Control traffic at the subnet level (stateless)
- Security Group example: Allow port 22 (SSH) from `0.0.0.0/0`

---

### 5. **VPC Peering / VPN / Direct Connect**
- **VPC Peering**: Private communication between two VPCs
- **VPN Gateway**: Secure tunnel between on-prem and AWS
- **Direct Connect**: Dedicated fiber connection between AWS and on-prem

---

📌 _These slices together form a secure and scalable cloud network similar to a traditional hardware infrastructure._
