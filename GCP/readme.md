# ☁️ GCP Cheatsheet

> 🚀 Complete Google Cloud Platform (GCP) Guide for Beginners to Advanced Users  
> 🌐 Learn GCP Compute, Storage, Networking, Security, Kubernetes, Monitoring & Best Practices

---

# 📚 Table of Contents

1. Introduction  
2. Core GCP Services  
3. Networking  
4. Security and Identity  
5. Management Tools  
6. Advanced Topics  
7. Best Practices  
8. References  

---

# 🚀 1. Introduction

## 🔹 What is GCP?

Google Cloud Platform (GCP) is a suite of cloud computing services offered by Google. It provides a range of services including compute, storage, databases, machine learning, and more.

---

# ⚙️ 2. Core GCP Services

## 🖥️ Compute

### 🔹 Google Compute Engine (GCE)

Scalable virtual machines running on Google’s infrastructure.

#### Key Concepts

- Machine Types
- Images
- Snapshots
- Persistent Disks

#### Example

```bash
gcloud compute instances create my-instance \
--zone=us-central1-a \
--machine-type=e2-medium \
--image-family=debian-10 \
--image-project=debian-cloud
```

---

### 🔹 Google Kubernetes Engine (GKE)

Managed Kubernetes service for running containerized applications.

#### Key Concepts

- Clusters
- Nodes
- Pods
- Services
- Deployments

#### Example

```bash
gcloud container clusters create my-cluster \
--zone us-central1-a \
--num-nodes 3
```

---

### 🔹 Cloud Functions

Serverless environment to execute code in response to events.

#### Key Concepts

- Functions
- Triggers
- Event Sources

#### Example

```bash
gcloud functions deploy my-function \
--runtime python39 \
--trigger-http \
--allow-unauthenticated
```

---

## 💾 Storage

### 🔹 Google Cloud Storage

Object storage service for storing and accessing data.

#### Key Concepts

- Buckets
- Objects
- Classes
  - Standard
  - Nearline
  - Coldline
  - Archive

#### Example

```bash
gsutil mb gs://my-bucket
```

```bash
gsutil cp my-file.txt gs://my-bucket/
```

---

### 🔹 Persistent Disks

Durable, high-performance block storage for VM instances.

#### Key Concepts

- Disk Types
  - Standard
  - SSD
  - Balanced
- Snapshots
- Zonal/Regional Disks

#### Example

```bash
gcloud compute disks create my-disk \
--size=100GB \
--type=pd-ssd \
--zone=us-central1-a
```

---

### 🔹 Filestore

Fully managed file storage service for applications that require a file system interface.

#### Key Concepts

- Instances
- Tiers
  - Basic
  - High Scale
  - Enterprise

#### Example

```bash
gcloud filestore instances create my-filestore-instance \
--zone=us-central1-a \
--tier=STANDARD \
--file-share=name="my-share",capacity=1TB \
--network=name="default"
```

---

# 🌐 3. Networking

## 🔹 VPC (Virtual Private Cloud)

Isolated network environments within GCP.

#### Key Concepts

- Subnets
- Routes
- Firewalls
- VPN
- Interconnect

#### Example

```bash
gcloud compute networks create my-vpc --subnet-mode=custom
```

```bash
gcloud compute networks subnets create my-subnet \
--network=my-vpc \
--region=us-central1 \
--range=10.0.0.0/24
```

---

# 🔐 4. Security and Identity

## 🔹 Identity and Access Management (IAM)

Manage access to resources with fine-grained control.

#### Key Concepts

- Roles
- Permissions
- Policies
- Service Accounts

#### Example

```bash
gcloud projects add-iam-policy-binding my-project \
--member="user:example@gmail.com" \
--role="roles/editor"
```

---

## 🔹 Cloud Key Management Service (KMS)

Create, manage, and use cryptographic keys.

#### Key Concepts

- Key Rings
- Keys
- Versions
- Policies

#### Example

```bash
gcloud kms keyrings create my-keyring --location=global
```

```bash
gcloud kms keys create my-key \
--keyring=my-keyring \
--location=global \
--purpose=encryption
```

---

# 🛠️ 5. Management Tools

## 🔹 Deployment Manager

Infrastructure as Code service for managing GCP resources.

#### Example

```bash
gcloud deployment-manager deployments create my-deployment \
--config=config.yaml
```

---

## 🔹 Stackdriver (Operations Suite)

Monitoring, logging, and diagnostics tool for GCP.

#### Example

```bash
gcloud logging write my-log \
"This is a log entry" \
--severity=ERROR
```

---

# 🚀 6. Advanced Topics

## 🔹 Auto Scaling

Automatically adjust VM instances based on demand.

#### Example

```bash
gcloud compute instance-groups managed set-autoscaling my-group \
--max-num-replicas 10 \
--min-num-replicas 1 \
--target-cpu-utilization 0.6
```

---

## 🔹 Serverless Architectures

Use Cloud Functions, Cloud Run, and Pub/Sub for serverless solutions.

#### Example

```bash
gcloud run deploy my-service \
--image=gcr.io/my-project/my-image \
--platform managed
```

---

# ✅ 7. Best Practices

## 🔹 Security

- Use IAM policies properly
- Encrypt sensitive data
- Enable audit logging
- Monitor infrastructure regularly

---

## 🔹 Reliability

- Use multiple zones/regions
- Configure backups
- Use load balancing
- Enable monitoring

---

## 🔹 Cost Optimization

- Delete unused resources
- Monitor billing
- Use committed use discounts
- Optimize storage lifecycle policies

---

# 📚 8. References

## 🔹 Official Documentation

- Google Cloud Documentation
- GCP CLI Documentation
- GKE Documentation

---

# 🎯 Final Takeaway

Google Cloud Platform (GCP) provides scalable, secure, and reliable cloud services for modern applications.

It helps teams:

- Build cloud-native applications
- Automate infrastructure
- Run Kubernetes workloads
- Implement DevOps practices
- Scale applications globally

---

<p align="center">

☁️ GCP Powers Modern Cloud Infrastructure 🚀

</p>
