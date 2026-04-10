 # 🔐 AWS IAM (Identity and Access Management)

> 📚 Complete IAM Guide (Beginner → Intermediate → Practical)  
> ⚡ IAM is the core security service of AWS

---

# 🔹 What is IAM?

IAM is an AWS service that controls access to AWS resources by defining:
- Who can access resources
- What actions they can perform
- How they can access those resources

---

# 🔹 Why IAM is Needed?

AWS environments involve multiple users and services interacting with resources.

Without IAM:
- There would be no access control
- Anyone could access or modify resources
- It would create major security risks

---

# 🔹 IAM Working Flow

1. A request is made to AWS  
2. AWS authenticates the identity  
3. AWS evaluates permissions using policies  
4. Access is allowed or denied  

👉 Default behavior: **Deny**

---

# 🔥 IAM Components

## 🔹 Users

A user is an individual identity in AWS with credentials and permissions.

---

## 🔹 Groups

A group is a collection of users that share the same permissions.

---

## 🔹 Roles

A role is a set of temporary permissions that can be assumed by users or AWS services.

- Roles do not have permanent credentials  
- Used for secure access  

---

## 🔹 Policies

Policies are JSON documents that define permissions using Allow or Deny rules.

---

# 🔥 Types of Policies

## 🔹 Managed Policies

- Predefined policies created by AWS  
- Can be reused across multiple identities  

---

## 🔹 Inline Policies

- Custom policies created and attached directly  
- One-to-one relationship with user/group/role  

---

# 🔐 Authentication and Authorization

## 🔹 Authentication

Authentication is the process of verifying the identity of a user.

---

## 🔹 Authorization

Authorization is the process of granting or denying permissions to a user.

---

# 🔥 IAM Best Practices

## 🔹 Least Privilege

Grant only the permissions that are necessary.

---

## 🔹 Use Groups

Assign permissions to groups instead of individual users.

---

## 🔹 Enable MFA

Use multi-factor authentication for additional security.

---

## 🔹 Rotate Credentials

Regularly update passwords and access keys.

---

# 🔥 IAM Roles and Use Cases

## 🔹 Roles for Compute Services

Attach roles to compute resources to allow secure access to AWS services without using credentials.

---

## 🔹 Cross-Account Access

Allows access to resources between different AWS accounts using role assumption.

---

# 🔍 IAM Security Tools

## 🔹 CloudTrail

Records all API calls and IAM-related activities for auditing and monitoring.

---

## 🔹 Access Analyzer

Identifies resources that are accessible from outside the AWS account.

---

# 🔐 Temporary Credentials

## 🔹 STS (Security Token Service)

Provides temporary security credentials for accessing AWS resources.

---

## 🔹 Use Cases

- Federated access (e.g., external login providers)  
- Cross-account access  
- Temporary elevated permissions  

---

# 🔥 IAM Policy Structure

## 🔹 Version

Specifies the policy language version.

---

## 🔹 Statement

Main block where permissions are defined.

---

## 🔹 Effect

Defines whether access is allowed or denied.

---

## 🔹 Action

Specifies what actions are allowed or denied.

---

## 🔹 Resource

Specifies the resource on which actions apply.

---

## 🔹 Condition

Defines conditions under which the policy is applied.

---

# 🧠 Final Concept

IAM works by:
- Authenticating identities  
- Authorizing actions using policies  

👉 Final decision is always:
**Allow or Deny (default is Deny)**

---
