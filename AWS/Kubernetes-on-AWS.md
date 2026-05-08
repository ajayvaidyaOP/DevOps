# ☸️ Kubernetes on AWS Cheatsheet

> 🚀 Complete Kubernetes on AWS (EKS) Guide  
> 🔄 Learn Amazon EKS Setup, Networking, Deployments, Storage, Monitoring, Security & Auto Scaling

---

# 📚 Table of Contents

1. Introduction to Kubernetes on AWS  
2. Setting Up Kubernetes on AWS  
3. EKS Cluster Configuration  
4. Networking  
5. Deploying Applications  
6. Storage  
7. Monitoring and Logging  
8. Security  
9. Auto Scaling and Load Balancing  
10. Backup and Recovery  
11. Upgrades and Maintenance  
12. References  

---

# 🚀 1. Introduction to Kubernetes on AWS

## 🔹 What is Kubernetes?

Kubernetes is an open-source platform for automating containerized application deployment, scaling, and management.

---

## 🔹 Kubernetes on AWS

AWS offers managed Kubernetes services through Amazon EKS (Elastic Kubernetes Service), simplifying Kubernetes cluster management on AWS infrastructure.

---

# ⚙️ 2. Setting Up Kubernetes on AWS

## 🔹 Amazon EKS Overview

Amazon EKS is a managed Kubernetes service that:

- Handles the control plane
- Integrates with AWS services
- Simplifies cluster operations

---

## 🔹 Creating an EKS Cluster

### Using AWS CLI

```bash
aws eks create-cluster \
--name my-cluster \
--role-arn arn:aws:iam::123456789012:role/EKS-Cluster-Role \
--resources-vpc-config subnetIds=subnet-0bb1c79de4EXAMPLE,subnet-0bb1c79de4EXAMPLE
```

---

## 🔹 Configure kubectl

```bash
aws eks update-kubeconfig --name my-cluster
```

---

# ⚙️ 3. EKS Cluster Configuration

## 🔹 Node Groups

### Create Node Group

```bash
aws eks create-nodegroup \
--cluster-name my-cluster \
--nodegroup-name my-node-group \
--scaling-config minSize=1,maxSize=3,desiredSize=2 \
--disk-size 20 \
--subnets subnet-0bb1c79de4EXAMPLE,subnet-0bb1c79de4EXAMPLE \
--instance-types t3.medium \
--node-role arn:aws:iam::123456789012:role/EKS-Node-Role
```

---

## 🔹 IAM Roles and Policies

### Important Policies

- AmazonEKSClusterPolicy
- AmazonEKSWorkerNodePolicy
- AmazonEC2ContainerRegistryReadOnly

---

# 🌐 4. Networking

## 🔹 Create VPC

```bash
aws ec2 create-vpc --cidr-block 10.0.0.0/16
```

---

## 🔹 Create Subnet

```bash
aws ec2 create-subnet \
--vpc-id vpc-0bb1c79de4EXAMPLE \
--cidr-block 10.0.1.0/24 \
--availability-zone us-west-2a
```

---

## 🔹 Amazon VPC CNI Plugin

```bash
kubectl apply -f \
https://raw.githubusercontent.com/aws/amazon-vpc-cni-k8s/master/config/v1.12/aws-k8s-cni.yaml
```

---

# 🚀 5. Deploying Applications

## 🔹 Deployment Example

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment

spec:
  replicas: 2

  selector:
    matchLabels:
      app: my-app

  template:
    metadata:
      labels:
        app: my-app

    spec:
      containers:
      - name: my-container
        image: my-image:latest

        ports:
        - containerPort: 80
```

---

## 🔹 Apply Deployment

```bash
kubectl apply -f deployment.yaml
```

---

## 🔹 Service Example

```yaml
apiVersion: v1
kind: Service

metadata:
  name: my-service

spec:
  selector:
    app: my-app

  ports:
  - protocol: TCP
    port: 80
    targetPort: 80

  type: LoadBalancer
```

---

## 🔹 Apply Service

```bash
kubectl apply -f service.yaml
```

---

## 🔹 Install NGINX Ingress Controller

```bash
kubectl apply -f \
https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/aws/deploy.yaml
```

---

## 🔹 Ingress Example

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress

metadata:
  name: my-ingress

spec:
  rules:
  - host: myapp.example.com

    http:
      paths:
      - path: /

        pathType: Prefix

        backend:
          service:
            name: my-service

            port:
              number: 80
```

---

# 💾 6. Storage

## 🔹 Create EBS Volume

```bash
aws ec2 create-volume \
--size 10 \
--availability-zone us-west-2a \
--volume-type gp2
```

---

## 🔹 Attach EBS Volume

```bash
aws ec2 attach-volume \
--volume-id vol-0bb1c79de4EXAMPLE \
--instance-id i-0bb1c79de4EXAMPLE \
--device /dev/xvdf
```

---

## 🔹 Persistent Volume Example

```yaml
apiVersion: v1
kind: PersistentVolume

metadata:
  name: my-pv

spec:
  capacity:
    storage: 10Gi

  accessModes:
    - ReadWriteOnce

  hostPath:
    path: /mnt/data
```

---

## 🔹 Persistent Volume Claim

```yaml
apiVersion: v1
kind: PersistentVolumeClaim

metadata:
  name: my-pvc

spec:
  accessModes:
    - ReadWriteOnce

  resources:
    requests:
      storage: 10Gi
```

---

# 📊 7. Monitoring and Logging

## 🔹 Install CloudWatch Agent

```bash
kubectl apply -f \
https://s3.amazonaws.com/amazoncloudwatch-agent-kubernetes/amazon-cloudwatch-agent.yaml
```

---

## 🔹 Install Prometheus

```bash
kubectl create namespace monitoring
```

```bash
kubectl apply -f \
https://github.com/prometheus/prometheus/releases/download/v2.26.0/prometheus-2.26.0.yaml
```

---

## 🔹 Install Grafana

```bash
kubectl apply -f \
https://raw.githubusercontent.com/grafana/grafana/main/deploy/kubernetes/grafana-deployment.yaml
```

---

# 🔐 8. Security

## 🔹 IAM Role for Service Account

### Create IAM Role

```bash
aws iam create-role \
--role-name my-k8s-role \
--assume-role-policy-document file://trust-policy.json
```

---

## 🔹 Attach Policy

```bash
aws iam attach-role-policy \
--role-name my-k8s-role \
--policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```

---

## 🔹 Kubernetes Service Account

```yaml
apiVersion: v1
kind: ServiceAccount

metadata:
  name: my-service-account

annotations:
  eks.amazonaws.com/role-arn: \
arn:aws:iam::123456789012:role/my-k8s-role
```

---

## 🔹 Network Policy Example

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy

metadata:
  name: allow-front-end

spec:
  podSelector:
    matchLabels:
      role: front-end

  ingress:
  - from:
    - podSelector:
        matchLabels:
          role: back-end
```

---

## 🔹 Create Secret

```bash
kubectl create secret generic my-secret \
--from-literal=password=my-password
```

---

# ⚖️ 9. Auto Scaling and Load Balancing

## 🔹 Horizontal Pod Autoscaler

```bash
kubectl autoscale deployment my-deployment \
--cpu-percent=50 \
--min=1 \
--max=10
```

---

## 🔹 Cluster Autoscaler

```bash
kubectl apply -f \
https://github.com/kubernetes/autoscaler/releases/download/<version>/cluster-autoscaler-v<version>.yaml
```

---

## 🔹 LoadBalancer Service

```yaml
apiVersion: v1
kind: Service

metadata:
  name: my-service

spec:
  type: LoadBalancer

  selector:
    app: my-app

  ports:
  - protocol: TCP
    port: 80
    targetPort: 80
```

---

# 💽 10. Backup and Recovery

## 🔹 Create EBS Snapshot

```bash
aws ec2 create-snapshot \
--volume-id vol-0bb1c79de4EXAMPLE \
--description "My snapshot"
```

---

## 🔹 Restore Snapshot

```bash
aws ec2 create-volume \
--snapshot-id snap-0bb1c79de4EXAMPLE \
--availability-zone us-west-2a
```

---

## 🔹 Install Velero

```bash
velero install \
--provider aws \
--bucket <bucket-name> \
--secret-file <credentials-file> \
--backup-location-config region=<region>
```

---

## 🔹 Create Backup

```bash
velero backup create my-backup \
--include-namespaces my-namespace
```

---

# 🔄 11. Upgrades and Maintenance

## 🔹 Upgrade EKS Cluster

```bash
aws eks update-cluster-version \
--name my-cluster \
--kubernetes-version 1.21
```

---

## 🔹 Upgrade Node Group

```bash
aws eks update-nodegroup-version \
--cluster-name my-cluster \
--nodegroup-name my-node-group \
--release-version 1.21
```

---

## 🔹 Maintenance Best Practices

- Monitor cluster health
- Scan images regularly
- Apply security patches
- Update Kubernetes versions
- Enable logging and monitoring

---

# 📚 12. References

## 🔹 Official Documentation

- Amazon EKS Documentation
- Kubernetes Documentation

---

## 🔹 Tools and Resources

- AWS CLI Documentation
- kubectl Documentation

---

# 🎯 Final Takeaway

Kubernetes on AWS with Amazon EKS helps teams:

- Deploy containerized applications
- Automate scaling and recovery
- Simplify Kubernetes management
- Integrate AWS cloud services
- Build highly available cloud-native applications

---

<p align="center">

☸️ Kubernetes + AWS EKS = Powerful Cloud Native Platform 🚀

</p>
