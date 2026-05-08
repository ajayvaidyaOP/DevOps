# 📂 AWS EFS Cheatsheet

> 🚀 Complete Amazon Elastic File System (EFS) Guide for Beginners to Advanced Users  
> ☁️ Learn EFS Architecture, Mounting, Security, Performance, Backup & Kubernetes Integration

---

# 📚 Table of Contents

1. Introduction to AWS EFS  
2. EFS Key Concepts  
3. Creating EFS  
4. Mounting EFS  
5. EFS Performance Modes  
6. EFS Storage Classes  
7. EFS Security  
8. EFS with EC2  
9. EFS with Kubernetes/EKS  
10. Backup & Monitoring  
11. Troubleshooting EFS  
12. References  

---

# 🚀 1. Introduction to AWS EFS

## 🔹 What is AWS EFS?

Amazon Elastic File System (EFS) is a fully managed, scalable, and elastic Network File System (NFS) service provided by AWS.

EFS allows multiple EC2 instances to access the same shared file system simultaneously.

---

## 🔑 Key Features of AWS EFS

| Feature | Description |
|---|---|
| Fully Managed | AWS manages infrastructure automatically |
| Shared Storage | Multiple servers can access same data |
| Elastic Scaling | Automatically grows and shrinks |
| NFS Protocol | Uses standard NFSv4 protocol |
| High Availability | Multi-AZ availability |
| Secure | Supports encryption and IAM policies |

---

## 🔹 Important AWS EFS Definitions

| Term | Definition |
|---|---|
| File System | Main EFS storage resource |
| Mount Target | Network endpoint inside a subnet |
| Access Point | Application-specific entry point |
| NFS | Network File System protocol |
| Throughput Mode | Controls file system throughput |
| Performance Mode | Defines latency and scalability |
| Lifecycle Policy | Automatically moves old files to IA storage |
| General Purpose Mode | Low latency performance mode |
| Max I/O Mode | High throughput scalable mode |
| Encryption at Rest | Encrypts stored data |
| Encryption in Transit | Encrypts data while transferring |

---

# 🛠️ 2. EFS Key Concepts

## 🔹 EFS Architecture

```text
EC2 Instances
      │
      ▼
Mount Target (Subnet)
      │
      ▼
Amazon EFS File System
```

---

## 🔹 EFS Use Cases

Common use cases:

- Shared application storage
- Web server content sharing
- Kubernetes persistent storage
- Big data analytics
- Home directories
- Content management systems

---

## 🔹 EFS vs EBS vs S3

| Service | Type | Usage |
|---|---|---|
| EFS | File Storage | Shared storage |
| EBS | Block Storage | Single EC2 storage |
| S3 | Object Storage | Backup/static files |

---

# ⚙️ 3. Creating EFS

## 🔹 Create EFS via AWS Console

Steps:

1. Open AWS Console  
2. Go to EFS Service  
3. Click Create File System  
4. Select VPC  
5. Configure Security Groups  
6. Create Mount Targets  
7. Create File System  

---

## 🔹 Create EFS using AWS CLI

```bash
aws efs create-file-system \
--creation-token my-efs
```

---

## 🔹 Create Mount Target

```bash
aws efs create-mount-target \
--file-system-id fs-12345678 \
--subnet-id subnet-123456 \
--security-groups sg-123456
```

---

# 🔗 4. Mounting EFS

## 🔹 Install NFS Utilities

### Amazon Linux / RHEL

```bash
sudo yum install -y amazon-efs-utils
```

---

### Ubuntu

```bash
sudo apt update
sudo apt install nfs-common -y
```

---

## 🔹 Create Mount Directory

```bash
sudo mkdir /efs
```

---

## 🔹 Mount EFS

```bash
sudo mount -t efs fs-12345678:/ /efs
```

---

## 🔹 Mount using NFS

```bash
sudo mount -t nfs4 \
fs-12345678.efs.us-east-1.amazonaws.com:/ /efs
```

---

## 🔹 Persistent Mount in fstab

```bash
fs-12345678:/ /efs efs defaults,_netdev 0 0
```

---

# ⚡ 5. EFS Performance Modes

## 🔹 General Purpose Mode

Used for:

- Low latency workloads
- Web applications
- CMS systems

---

## 🔹 Max I/O Mode

Used for:

- High throughput workloads
- Big data applications
- Parallel processing

---

## 🔹 Throughput Modes

| Mode | Description |
|---|---|
| Bursting | Default automatic throughput |
| Provisioned | User-defined throughput |
| Elastic | Automatically scales throughput |

---

# 💾 6. EFS Storage Classes

## 🔹 Standard Storage

Used for:

- Frequently accessed files
- Low latency access

---

## 🔹 Infrequent Access (IA)

Used for:

- Rarely accessed data
- Cost optimization

---

## 🔹 Archive Storage

Used for:

- Long-term archival
- Lowest storage cost

---

## 🔹 Lifecycle Policy Example

Automatically move files:

```text
30 days → EFS IA
90 days → EFS Archive
```

---

# 🔐 7. EFS Security

## 🔹 Security Groups

Allow NFS traffic:

```text
Port: 2049
Protocol: TCP
```

---

## 🔹 Encryption at Rest

Enable AWS KMS encryption during EFS creation.

---

## 🔹 Encryption in Transit

Mount securely:

```bash
sudo mount -t efs -o tls fs-12345678:/ /efs
```

---

## 🔹 IAM Policies

Control EFS access using IAM permissions.

---

## 🔹 Access Points

Used for:

- Application isolation
- Custom POSIX permissions
- Secure access

---

# 🖥️ 8. EFS with EC2

## 🔹 Shared Storage Across EC2

Multiple EC2 instances can access:

```text
/efs
```

simultaneously.

---

## 🔹 Common EC2 Use Cases

- Shared uploads folder
- Shared website content
- Shared logs
- Shared configuration

---

## 🔹 Verify Mounted Storage

```bash
df -h
```

---

## 🔹 Test Shared File

```bash
echo "Hello EFS" > /efs/test.txt
```

---

# ☸️ 9. EFS with Kubernetes/EKS

## 🔹 Why Use EFS in Kubernetes?

EFS provides:

- Persistent shared storage
- Multi-pod access
- Dynamic provisioning

---

## 🔹 Install EFS CSI Driver

```bash
kubectl apply -k \
github.com/kubernetes-sigs/aws-efs-csi-driver/deploy/kubernetes/overlays/stable
```

---

## 🔹 Persistent Volume Example

```yaml
apiVersion: v1
kind: PersistentVolume

metadata:
  name: efs-pv

spec:
  capacity:
    storage: 5Gi

  accessModes:
    - ReadWriteMany

  csi:
    driver: efs.csi.aws.com
    volumeHandle: fs-12345678
```

---

## 🔹 Persistent Volume Claim Example

```yaml
apiVersion: v1
kind: PersistentVolumeClaim

metadata:
  name: efs-pvc

spec:
  accessModes:
    - ReadWriteMany

  resources:
    requests:
      storage: 5Gi
```

---

# 📊 10. Backup & Monitoring

## 🔹 AWS Backup for EFS

Used for:

- Automated backups
- Disaster recovery
- Retention policies

---

## 🔹 Monitor EFS using CloudWatch

Important metrics:

| Metric | Purpose |
|---|---|
| BurstCreditBalance | Available throughput credits |
| PercentIOLimit | I/O utilization |
| ClientConnections | Connected clients |
| DataReadIOBytes | Read throughput |
| DataWriteIOBytes | Write throughput |

---

## 🔹 CloudWatch Alarm Example

Monitor:

- High throughput
- Low credits
- High latency

---

# 🛠️ 11. Troubleshooting EFS

## 🔹 Common Issues

| Issue | Solution |
|---|---|
| Mount Failure | Check security groups |
| Permission Denied | Verify IAM and POSIX permissions |
| Timeout Error | Verify NFS port 2049 |
| Slow Performance | Check throughput mode |
| DNS Resolution Failed | Verify VPC DNS settings |

---

## 🔹 Verify NFS Connectivity

```bash
telnet fs-12345678.efs.us-east-1.amazonaws.com 2049
```

---

## 🔹 Check Mounted File Systems

```bash
mount | grep efs
```

---

## 🔹 View EFS Logs

```bash
sudo journalctl -xe
```

---

# 📚 12. References

## 🔹 Official Documentation

- AWS EFS Documentation
- AWS EFS CSI Driver
- AWS Backup Documentation

---

## 🔹 Community Resources

- AWS Labs GitHub
- Kubernetes EFS Examples
- DevOps EFS Tutorials

---

# 🎯 Final Takeaway

Amazon EFS is a scalable and highly available shared file storage service for AWS workloads.

It helps DevOps teams:

- Share storage across servers
- Simplify Kubernetes persistence
- Improve scalability
- Reduce storage management overhead
- Build highly available applications

---

<p align="center">

📂 AWS EFS Enables Scalable Shared Storage 🚀

</p>
