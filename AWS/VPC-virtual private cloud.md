# 🌐 AWS VPC (Virtual Private Cloud)

> 📚 Complete VPC Guide (Beginner → Intermediate → Practical)  
> ⚡ Networking foundation of AWS

---

# 🔹 What is VPC?

Amazon VPC is a logically isolated virtual network in AWS where you can launch and manage resources securely.

👉 It allows you to:
- Define your own network  
- Control IP ranges  
- Manage routing and security  

---

# 🔹 Why VPC is Needed?

- Isolated environment for resources  
- Full control over networking  
- Secure communication between services  
- Required for production-grade architecture  

---

# 🔹 Core Components of VPC

---

## 🔹 CIDR Block

A CIDR block defines the IP address range of the VPC.

👉 Example:
10.0.0.0/16

---

## 🔹 Subnet

A subnet is a smaller network inside a VPC.

### Types:
- Public Subnet → Has internet access  
- Private Subnet → No direct internet access  

---

## 🔹 Internet Gateway (IGW)

Allows communication between VPC and the internet.

👉 Attached to VPC  

---

## 🔹 Route Table

Defines how traffic flows in the VPC.

👉 Contains rules:
- Destination → Target  

---

## 🔹 NAT Gateway

Allows private subnet resources to access the internet (outbound only).

👉 Used for updates, downloads  

---

## 🔹 Security Group

Acts as a virtual firewall at instance level.

---

## 🔹 Network ACL (NACL)

Acts as a firewall at subnet level.

---

# 🔹 How VPC Works

1. Create VPC with CIDR  
2. Create subnets (public/private)  
3. Attach Internet Gateway  
4. Configure route tables  
5. Launch resources in subnets  

---

# 🔥 Public vs Private Subnet

## 🔹 Public Subnet

- Has route to Internet Gateway  
- Used for:
  - Web servers  
  - Load balancers  

---

## 🔹 Private Subnet

- No direct internet access  
- Used for:
  - Databases  
  - Backend services  

---

# 🔥 Security in VPC

## 🔹 Security Group

- Stateful  
- Instance level  
- Only allow rules  

---

## 🔹 NACL

- Stateless  
- Subnet level  
- Allow and Deny rules  

---

# 🔍 Key Differences

| Feature        | Security Group | NACL |
|---------------|--------------|------|
| Level         | Instance     | Subnet |
| Type          | Stateful     | Stateless |
| Rules         | Allow only   | Allow & Deny |

---

# 🔄 Real Use Case Architecture

👉 Typical 3-tier architecture:

- Public Subnet:
  - Load Balancer  

- Private Subnet:
  - Application servers  

- Private Subnet:
  - Database  

---

# ⚠️ Common Mistakes

- Incorrect route tables  
- Missing IGW  
- Wrong security group rules  
- Exposing private resources  

---

# 🔒 Best Practices

- Use private subnets for backend  
- Restrict inbound traffic  
- Use NAT Gateway for outbound access  
- Design proper CIDR range  
- Use multiple AZs  

---

# 🏆 Interview Questions

- What is VPC?  
- Difference between public and private subnet?  
- What is NAT Gateway?  
- Difference between SG and NACL?  
- What is CIDR?  

---

# 🧪 Practical Steps

## Create VPC

1. Go to VPC Dashboard  
2. Click Create VPC  
3. Enter CIDR block  
4. Create  

---

## Create Subnet

1. Select VPC  
2. Create subnet  
3. Choose AZ  
4. Assign CIDR  

---

## Enable Internet Access

1. Create Internet Gateway  
2. Attach to VPC  
3. Update route table (0.0.0.0/0 → IGW)  

---

# 💡 Quick Revision

VPC = Network  
Subnet = Sub-network  
IGW = Internet access  
NAT = Outbound internet  
SG = Instance firewall  
NACL = Subnet firewall  

---

# 🎯 Final Concept

VPC is the networking backbone of AWS that provides a secure and customizable environment to run cloud resources.
