# 🖥️ AWS EC2 (Elastic Compute Cloud)

> 📚 Complete EC2 Guide (Beginner → Intermediate → Practical)  
> ⚡ Core compute service of AWS used to run virtual servers

---

# 🔹 What is EC2?

Amazon EC2 is a service that provides virtual servers (instances) in the cloud.

👉 It allows you to:
- Run applications  
- Host websites  
- Deploy services  

---

# 🔹 Why EC2 is Needed?

- No need to buy physical servers  
- Scalable infrastructure  
- Full control over OS and configuration  
- Pay-as-you-go pricing  

---

# 🔹 Basic Terminology

## 🔹 Instance
A virtual server in AWS.

## 🔹 AMI (Amazon Machine Image)
A pre-configured template used to launch instances.

## 🔹 Instance Type
Defines CPU, RAM, and performance.

## 🔹 Key Pair
Used for secure login (SSH).

## 🔹 Security Group
Acts as a virtual firewall controlling inbound and outbound traffic.

---

# 🔹 How EC2 Works

1. Select AMI  
2. Choose instance type  
3. Configure network and security  
4. Launch instance  
5. Connect using SSH or RDP  

---

# 🔥 EC2 Instance Types

## 🔹 General Purpose
Balanced CPU and memory (e.g., t3)

## 🔹 Compute Optimized
High CPU performance

## 🔹 Memory Optimized
High RAM workloads

## 🔹 Storage Optimized
High disk throughput

---

# 🔥 EC2 Pricing Models

## 🔹 On-Demand
Pay per usage (no commitment)

## 🔹 Reserved Instances
Long-term commitment (lower cost)

## 🔹 Spot Instances
Very low cost (can be interrupted)

---

# 🔐 EC2 Security

## 🔹 Security Groups
- Allow/Deny traffic  
- Works at instance level  

## 🔹 Key Pair
- Private key for SSH access  
- Must be kept secure  

## 🔹 IAM Role
- Used to give EC2 access to other AWS services  
- Avoid using access keys  

---

# 🌐 Networking Basics

- Each EC2 runs inside a VPC  
- Uses private and public IP  
- Internet access via Internet Gateway  

---

# 🔄 Storage Options

## 🔹 EBS (Elastic Block Storage)
- Persistent storage  
- Attached to instance  

## 🔹 Instance Store
- Temporary storage  
- Data lost on stop/terminate  

---

# 🔁 EC2 Lifecycle

- Pending → Running → Stopped → Terminated  

---

# 🔄 Real Use Cases

- Web hosting  
- Application servers  
- CI/CD pipelines  
- Backend services  

---

# ⚠️ Common Mistakes

- Opening all ports (0.0.0.0/0)  
- Losing private key  
- Not stopping unused instances  
- Hardcoding credentials  

---

# 🔒 Best Practices

- Use IAM roles instead of keys  
- Restrict security group access  
- Regularly monitor instances  
- Use proper instance types  
- Enable backups  

---

# 🏆 Interview Questions

- What is EC2?  
- What is AMI?  
- What is security group?  
- Difference between EBS and instance store?  
- What are pricing models?  

---

# 🧪 Practical Steps

## Launch EC2 Instance

1. Go to EC2 Dashboard  
2. Click Launch Instance  
3. Select AMI  
4. Choose instance type  
5. Configure security group  
6. Create/select key pair  
7. Launch  

---

## Connect to Instance (Linux)

```bash
ssh -i key.pem ec2-user@public-ip
