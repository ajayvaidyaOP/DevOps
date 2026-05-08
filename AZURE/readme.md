# ☁️ Azure Cheatsheet

> 🚀 Complete Microsoft Azure Guide for Beginners to Advanced Users  
> 🌐 Learn Azure Compute, Storage, Networking, Security, Kubernetes, Monitoring & Best Practices

---

# 📚 Table of Contents

1. Introduction  
2. Core Azure Services  
3. Networking  
4. Security and Identity  
5. Management Tools  
6. Advanced Topics  
7. Best Practices  

---

# 🚀 1. Introduction

## 🔹 What is Microsoft Azure?

Microsoft Azure is a cloud computing platform offering a wide range of services, including compute, analytics, storage, and networking.

---

# ⚙️ 2. Core Azure Services

## 🖥️ Compute

### 🔹 Azure Virtual Machines

Scalable virtual servers for running applications.

#### Key Concepts

- VM Sizes
- Resource Groups
- Virtual Networks
- Disks

#### Example

```bash
az vm create \
--resource-group myResourceGroup \
--name myVM \
--image UbuntuLTS \
--admin-username azureuser \
--generate-ssh-keys
```

---

### 🔹 Azure Functions

Serverless compute service for running event-driven code.

#### Key Concepts

- Functions
- Triggers
- Bindings

#### Example

```bash
func init MyFunctionProj --dotnet
```

```bash
func new \
--name MyHttpTrigger \
--template "HTTP trigger" \
--authlevel "anonymous"
```

---

### 🔹 Azure Kubernetes Service (AKS)

Managed Kubernetes service for running containerized applications.

#### Key Concepts

- Clusters
- Nodes
- Pods
- Services

#### Example

```bash
az aks create \
--resource-group myResourceGroup \
--name myAKSCluster \
--node-count 1 \
--enable-addons monitoring \
--generate-ssh-keys
```

---

## 💾 Storage

### 🔹 Azure Blob Storage

Object storage solution for the cloud.

#### Key Concepts

- Storage Accounts
- Containers
- Blobs
- Access Tiers

#### Example

```bash
az storage account create \
--name mystorageaccount \
--resource-group myResourceGroup \
--location eastus \
--sku Standard_LRS
```

```bash
az storage container create \
--name mycontainer \
--account-name mystorageaccount
```

```bash
az storage blob upload \
--container-name mycontainer \
--file myfile.txt \
--name myfile.txt \
--account-name mystorageaccount
```

---

### 🔹 Azure Files

Managed file shares in the cloud using the SMB protocol.

#### Key Concepts

- File Shares
- Directories
- Snapshots

#### Example

```bash
az storage share create \
--name myshare \
--account-name mystorageaccount
```

---

### 🔹 Azure Disk Storage

High-performance disk storage for VMs.

#### Key Concepts

- Managed Disks
- Disk Types
  - Standard HDD
  - Standard SSD
  - Premium SSD

#### Example

```bash
az disk create \
--resource-group myResourceGroup \
--name myDisk \
--size-gb 128 \
--sku Premium_LRS
```

---

## 🗄️ Database

### 🔹 Azure SQL Database

Managed relational database service.

#### Key Concepts

- Databases
- Servers
- Elastic Pools
- DTUs/vCores

#### Example

```bash
az sql db create \
--resource-group myResourceGroup \
--server myServer \
--name myDatabase \
--service-objective S0
```

---

### 🔹 Cosmos DB

Globally distributed, multi-model database service.

#### Key Concepts

- Databases
- Containers
- Partition Keys
- Consistency Levels

#### Example

```bash
az cosmosdb create \
--name myCosmosDBAccount \
--resource-group myResourceGroup \
--kind MongoDB \
--locations regionName=eastus
```

---

### 🔹 Azure Database for MySQL/PostgreSQL

Managed MySQL/PostgreSQL service.

#### Key Concepts

- Servers
- Databases
- Backup Retention
- Performance Tiers

#### Example

```bash
az mysql server create \
--resource-group myResourceGroup \
--name mydemoserver \
--location eastus \
--admin-user myadmin \
--admin-password mypassword \
--sku-name GP_Gen5_2
```

---

# 🌐 3. Networking

## 🔹 Azure Virtual Network (VNet)

Provides an isolated network environment in Azure.

#### Key Concepts

- Subnets
- Network Security Groups
- VPN Gateway
- Peering

#### Example

```bash
az network vnet create \
--resource-group myResourceGroup \
--name myVnet \
--address-prefix 10.0.0.0/16 \
--subnet-name mySubnet \
--subnet-prefix 10.0.1.0/24
```

---

## 🔹 Azure Load Balancer

Distributes inbound traffic across multiple VMs.

#### Key Concepts

- Frontend IP
- Backend Pools
- Load Balancing Rules

#### Example

```bash
az network lb create \
--resource-group myResourceGroup \
--name myLoadBalancer \
--frontend-ip-name myFrontEnd \
--backend-pool-name myBackEndPool
```

---

## 🔹 Azure Application Gateway

Web traffic load balancer for managing HTTP and HTTPS traffic.

#### Key Concepts

- Listener
- Rules
- HTTP Settings
- SSL Certificates

#### Example

```bash
az network application-gateway create \
--name myAppGateway \
--resource-group myResourceGroup \
--capacity 2 \
--sku Standard_v2 \
--vnet-name myVnet \
--subnet mySubnet
```

---

## 🔹 Azure DNS

Hosts DNS domains and provides name resolution using Azure infrastructure.

#### Key Concepts

- DNS Zones
- Records
- NS Records
- A Records

#### Example

```bash
az network dns zone create \
--resource-group myResourceGroup \
--name mydomain.com
```

```bash
az network dns record-set a add-record \
--resource-group myResourceGroup \
--zone-name mydomain.com \
--record-set-name www \
--ipv4-address 10.0.0.4
```

---

# 🔐 4. Security and Identity

## 🔹 Azure Active Directory (AAD)

Identity and access management service.

#### Key Concepts

- Users
- Groups
- Roles
- Managed Identities
- Conditional Access

#### Example

```bash
az ad user create \
--display-name "My User" \
--user-principal-name myuser@mydomain.com \
--password "P@ssw0rd!"
```

---

## 🔹 Azure Key Vault

Securely store and access secrets, keys, and certificates.

#### Key Concepts

- Vaults
- Secrets
- Keys
- Certificates
- Access Policies

#### Example

```bash
az keyvault create \
--name myKeyVault \
--resource-group myResourceGroup \
--location eastus
```

```bash
az keyvault secret set \
--vault-name myKeyVault \
--name MySecret \
--value "MySecretValue"
```

---

## 🔹 Azure Security Center

Unified infrastructure security management system.

#### Key Concepts

- Security Posture
- Recommendations
- Secure Score
- Just-in-Time VM Access

#### Example

```bash
az security assessment create \
--name myAssessment \
--status "Healthy" \
--description "This is a custom assessment."
```

---

## 🔹 Azure Policy

Enforce organizational standards and assess compliance at-scale.

#### Key Concepts

- Definitions
- Initiatives
- Assignments

#### Example

```bash
az policy assignment create \
--name myPolicyAssignment \
--scope /subscriptions/{subscription-id}/resourceGroups/{resource-group-name} \
--policy /subscriptions/{subscription-id}/providers/Microsoft.Authorization/policyDefinitions/{policyDefinitionName}
```

---

# 🛠️ 5. Management Tools

## 🔹 Azure Resource Manager (ARM)

Azure’s deployment and management service.

#### Key Concepts

- ARM Templates
- Resources
- Resource Groups
- Deployments

#### Example

```bash
az group create \
--name myResourceGroup \
--location eastus
```

```bash
az deployment group create \
--resource-group myResourceGroup \
--template-file azuredeploy.json
```

---

## 🔹 Azure Monitor

Comprehensive monitoring service for collecting, analyzing, and acting on telemetry data.

#### Key Concepts

- Metrics
- Logs
- Alerts
- Application Insights
- Log Analytics

#### Example

```bash
az monitor alert create \
--name myAlert \
--resource-group myResourceGroup \
--target /subscriptions/{subscription-id}/resourceGroups/{resource-group-name}/providers/Microsoft.Compute/virtualMachines/{vm-name} \
--condition "avg Percentage CPU > 75"
```

---

## 🔹 Azure Automation

Automate cloud management tasks.

#### Key Concepts

- Runbooks
- Desired State Configuration (DSC)
- Hybrid Worker Groups

#### Example

```bash
az automation account create \
--name myAutomationAccount \
--resource-group myResourceGroup \
--location eastus
```

```bash
az automation runbook create \
--name myRunbook \
--automation-account-name myAutomationAccount \
--resource-group myResourceGroup \
--type PowerShellWorkflow
```

---

## 🔹 Azure Advisor

Personalized cloud consultant that helps optimize Azure deployments.

#### Key Concepts

- Recommendations
- Cost
- Performance
- Security
- High Availability

---

# 🚀 6. Advanced Topics

## 🔹 Cost Management

Monitor and optimize Azure costs using Cost Management + Billing.

#### Example

```bash
az consumption budget create \
--amount 1000 \
--time-grain Monthly \
--start-date 2024-08-01 \
--end-date 2024-08-31 \
--name myBudget \
--resource-group myResourceGroup
```

---

## 🔹 Auto Scaling

Automatically adjust VM instances based on demand.

#### Key Concepts

- Scale Sets
- Scaling Rules
- Metrics

#### Example

```bash
az vmss create \
--resource-group myResourceGroup \
--name myScaleSet \
--image UbuntuLTS \
--upgrade-policy-mode automatic \
--admin-username azureuser \
--generate-ssh-keys
```

---

## 🔹 Serverless Architectures

Use Azure Functions, Logic Apps, and Event Grid for serverless solutions.

#### Key Concepts

- Triggers
- Bindings
- Workflows
- Event Subscriptions

#### Example

```bash
az eventgrid event-subscription create \
--name myEventSubscription \
--source-resource-id /subscriptions/{subscription-id}/resourceGroups/{resource-group}/providers/Microsoft.Storage/storageAccounts/{storage-account-name} \
--endpoint https://myfunction.azurewebsites.net/runtime/webhooks/eventgrid?functionName=myfunction
```

---

# ✅ 7. Best Practices

## 🔹 Security

- Use Azure Security Center
- Encrypt data
- Apply RBAC
- Monitor using Azure Monitor
- Implement secure coding practices

---

## 🔹 Reliability

- Use Availability Sets
- Use Availability Zones
- Configure backups
- Implement disaster recovery

---

## 🔹 Performance Efficiency

- Choose appropriate VM sizes
- Use caching services
- Optimize databases

---

## 🔹 Cost Optimization

- Use Reserved Instances (RIs)
- Monitor spending regularly
- Optimize unused resources

---

## 🔹 Operational Excellence

- Automate deployments using ARM
- Monitor operations continuously
- Use Infrastructure as Code (IaC)

---

# 🎯 Final Takeaway

Microsoft Azure provides scalable, secure, and enterprise-ready cloud services for modern applications.

It helps teams:

- Build cloud-native applications
- Deploy Kubernetes workloads
- Automate infrastructure
- Implement DevOps practices
- Scale applications globally

---

<p align="center">

☁️ Azure Powers Enterprise Cloud Infrastructure 🚀

</p>
