# 💽 AWS EBS (Elastic Block Store)

> 📚 Complete EBS Guide (Beginner → Intermediate → Practical)  
> ⚡ Persistent block storage for EC2 instances

---

# 🔹 What is EBS?

Amazon EBS is a block storage service that provides persistent storage volumes for EC2 instances.

👉 It is like a hard disk attached to a virtual machine.

---

# 🔹 Why EBS is Needed?

- Persistent storage (data remains after instance stop)  
- High performance storage  
- Suitable for databases and applications  
- Can be attached/detached from instances  

---

# 🔹 Key Concepts

## 🔹 Volume
A storage disk that can be attached to an EC2 instance.

## 🔹 Snapshot
A backup of an EBS volume stored in S3.

## 🔹 Availability Zone
EBS volumes are tied to a single AZ.

---

# 🔹 How EBS Works

1. Create EBS volume  
2. Attach it to EC2 instance  
3. Format and mount it  
4. Use it like a disk  

---

# 🔥 EBS Volume Types

## 🔹 gp3 (General Purpose SSD)
- Balanced performance  
- Default and most used  

---

## 🔹 io1 / io2 (Provisioned IOPS SSD)
- High performance  
- Used for critical workloads  

---

## 🔹 st1 (Throughput Optimized HDD)
- Big data workloads  

---

## 🔹 sc1 (Cold HDD)
- Low-cost storage  
- Infrequent access  

---

# 🔐 EBS Features

## 🔹 Persistence
Data remains even if instance stops.

---

## 🔹 Encryption
Supports encryption at rest using KMS.

---

## 🔹 Snapshots
- Backup stored in S3  
- Can restore volumes  

---

## 🔹 Elasticity
- Resize volumes  
- Change type  

---

# 🔄 Attach Types

## 🔹 Root Volume
- OS installed here  

## 🔹 Additional Volume
- Extra storage for apps/data  

---

# 🔄 Lifecycle

- Create → Attach → Use → Detach → Delete  

---

# 🌐 Performance

- Depends on volume type  
- IOPS and throughput configurable  

---

# 🔍 Real Use Cases

- Database storage  
- Application data  
- Boot volumes (OS)  
- Logs storage  

---

# ⚠️ Common Mistakes

- Not taking snapshots  
- Wrong volume type selection  
- Deleting volume accidentally  
- Not encrypting sensitive data  

---

# 🔒 Best Practices

- Use gp3 for general workloads  
- Take regular snapshots  
- Enable encryption  
- Monitor performance  
- Use proper sizing  

---

# 🏆 Interview Questions

- What is EBS?  
- Difference between EBS and S3?  
- What is snapshot?  
- What is gp3?  
- Is EBS AZ-specific?  

---

# 🧪 Practical Steps

## Create Volume

1. Go to EC2 Dashboard  
2. Click Volumes  
3. Create Volume  
4. Select type and size  
5. Choose AZ  

---

## Attach Volume

1. Select volume  
2. Click Attach  
3. Choose instance  

---

## Mount Volume (Linux)

```bash
lsblk
mkfs -t ext4 /dev/xvdf
mount /dev/xvdf /mnt
