# 🏗️ Terraform Cheatsheet

> 🚀 Complete Terraform Guide for Beginners to Advanced Users  
> ☁️ Learn Infrastructure as Code (IaC), Terraform Commands, State Management, Workspaces & Best Practices

---

# 📚 Table of Contents

1. Introduction to Terraform  
2. Key Terraform Concepts  
3. Beginner Terraform Commands  
4. Intermediate Terraform Commands  
5. Advanced Terraform Commands  
6. Common Terraform Workflows  
7. Terraform Best Practices  
8. Learning Resources  

---

# 🚀 1. Introduction to Terraform

## 🔹 What is Terraform?

Terraform by HashiCorp is an open-source Infrastructure as Code (IaC) tool used to provision and manage cloud, on-premises, and SaaS infrastructure using configuration files.

Terraform configurations are written using:

```text
HCL (HashiCorp Configuration Language)
```

Terraform helps teams:

- Automate infrastructure provisioning
- Reduce manual configuration
- Maintain consistent environments
- Manage multi-cloud infrastructure
- Track infrastructure changes

---

## 🔑 Key Features of Terraform

| Feature | Description |
|---|---|
| Infrastructure as Code | Manage infrastructure using code |
| Multi-Cloud Support | Works with AWS, Azure, GCP, Kubernetes, etc. |
| Declarative Syntax | Define desired infrastructure state |
| State Management | Tracks infrastructure changes |
| Reusable Modules | Create reusable infrastructure templates |
| Execution Plans | Preview infrastructure changes before apply |

---

# 📖 2. Key Terraform Concepts

## 🔹 Important Terraform Definitions

| Term | Definition |
|---|---|
| Provider | Plugin responsible for managing a cloud platform like AWS |
| Resource | Infrastructure object like EC2, S3, VPC, etc. |
| Variable | Input values passed into Terraform configuration |
| Output | Values returned after Terraform execution |
| State File | File that tracks Terraform-managed resources |
| Module | Reusable Terraform configuration block |
| Backend | Stores Terraform state remotely |
| Workspace | Separate environments like dev, stage, prod |
| Plan | Preview of infrastructure changes |
| Apply | Command used to create/update infrastructure |
| Destroy | Command used to delete infrastructure |
| HCL | HashiCorp Configuration Language |
| Provisioner | Used to execute scripts during resource creation |
| Data Source | Fetches existing infrastructure information |

---

# 🌍 3. Beginner Terraform Commands

## 🔹 Terraform Version

Shows installed Terraform version.

```bash
terraform version
```

---

## 🔹 Terraform Init

Initializes Terraform working directory.

```bash
terraform init
```

💡 Run once after creating `.tf` files.

---

## 🔹 Terraform Validate

Validates Terraform configuration syntax.

```bash
terraform validate
```

---

## 🔹 Terraform Plan

Shows infrastructure changes before applying.

```bash
terraform plan
```

📌 Always run before apply.

---

## 🔹 Terraform Apply

Creates or updates infrastructure.

```bash
terraform apply
```

### Auto Approve

```bash
terraform apply -auto-approve
```

---

## 🔹 Terraform Destroy

Deletes infrastructure resources.

```bash
terraform destroy
```

### Auto Confirm

```bash
terraform destroy -auto-approve
```

---

## 🔹 Terraform Format

Formats `.tf` files properly.

```bash
terraform fmt
```

### Recursive Format

```bash
terraform fmt -recursive
```

---

# ⚙️ 4. Intermediate Terraform Commands

## 🔹 Terraform Show

Displays Terraform state in readable format.

```bash
terraform show
```

```bash
terraform show terraform.tfstate
```

---

## 🔹 Terraform Output

Displays output variable values.

```bash
terraform output
```

### Specific Output

```bash
terraform output instance_ip
```

---

## 🔹 Terraform State List

Lists all resources inside state file.

```bash
terraform state list
```

---

## 🔹 Terraform State Show

Displays resource details from state.

```bash
terraform state show aws_instance.example
```

---

## 🔹 Terraform Taint

Marks resource for recreation.

```bash
terraform taint aws_instance.example
```

---

## 🔹 Terraform Untaint

Removes taint from resource.

```bash
terraform untaint aws_instance.example
```

---

## 🔹 Terraform Import

Imports existing infrastructure into Terraform state.

```bash
terraform import aws_instance.example i-0abcd1234efgh5678
```

---

## 🔹 Terraform Graph

Generates dependency graph.

```bash
terraform graph | dot -Tpng > graph.png
```

---

## 🔹 Terraform Providers

Lists providers used in configuration.

```bash
terraform providers
```

---

## 🔹 Terraform Workspace Commands

Used to manage multiple environments.

### Create Workspace

```bash
terraform workspace new dev
```

### Select Workspace

```bash
terraform workspace select dev
```

### List Workspaces

```bash
terraform workspace list
```

---

# 🚀 5. Advanced Terraform Commands

## 🔹 Save Execution Plan

```bash
terraform plan -out=tfplan
```

### Apply Saved Plan

```bash
terraform apply tfplan
```

---

## 🔹 Apply Specific Resource

```bash
terraform apply -target=aws_instance.example
```

---

## 🔹 Terraform State Move

Moves or renames resources in state.

```bash
terraform state mv aws_instance.old aws_instance.new
```

---

## 🔹 Terraform State Remove

Removes resource from state without deleting cloud resource.

```bash
terraform state rm aws_instance.example
```

---

## 🔹 Terraform Console

Interactive console for HCL expressions.

```bash
terraform console
```

### Example

```bash
> var.instance_type
```

---

## 🔹 Terraform Login

Authenticate with Terraform Cloud.

```bash
terraform login
```

---

## 🔹 Terraform Logout

Logout from Terraform Cloud.

```bash
terraform logout
```

---

## 🔹 Terraform Force Unlock

Unlocks locked Terraform state.

```bash
terraform force-unlock <LOCK_ID>
```

---

# 🔄 6. Common Terraform Workflows

## 🔹 New Project Workflow

```bash
terraform init
terraform plan
terraform apply
```

---

## 🔹 Update Infrastructure Workflow

```bash
terraform fmt
terraform validate
terraform plan
terraform apply
```

---

## 🔹 Destroy Infrastructure Workflow

```bash
terraform destroy
```

---

# ✅ 7. Terraform Best Practices

## 🔹 Secure State Files

Use remote backend:

- AWS S3
- DynamoDB Locking
- Terraform Cloud

---

## 🔹 Use Variables Properly

Use:

```text
terraform.tfvars
```

or

```text
.auto.tfvars
```

for reusable inputs.

---

## 🔹 Protect Sensitive Data

Mark outputs as sensitive:

```hcl
sensitive = true
```

---

## 🔹 Use Modules

Benefits:

- Reusability
- Cleaner code
- Standardization

---

## 🔹 Always Run Plan Before Apply

```bash
terraform plan
```

Helps prevent unexpected infrastructure changes.

---

## 🔹 Version Lock Providers

Example:

```hcl
required_providers {

  aws = {
    source  = "hashicorp/aws"
    version = "~> 5.0"
  }
}
```

---

# 📚 8. Learning Resources

## 🔹 Official Documentation

- Terraform Official Documentation
- Terraform CLI Reference

---

## 🔹 Terraform Registry

Used for:

- Providers
- Modules
- Examples

---

## 🔹 Learn Terraform

Free HashiCorp learning platform for beginners.

---

## 🔹 IaC Security Scanning

Popular tool:

- Checkov

---

# 🎯 Final Takeaway

Terraform is one of the most powerful Infrastructure as Code tools used in DevOps and Cloud Engineering.

It helps teams:

- Automate infrastructure
- Reduce manual errors
- Scale environments easily
- Maintain infrastructure consistency
- Implement DevOps automation efficiently

---

<p align="center">

🏗️ Terraform Automates Infrastructure Efficiently 🚀

</p>
