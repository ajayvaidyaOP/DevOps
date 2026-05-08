# ⎈ Helm Cheatsheet

> 🚀 Complete Helm Guide for Beginners to Advanced Users  
> 📦 Learn Helm Charts, Releases, Templates, Repositories, Hooks & Kubernetes Package Management

---

# 📚 Table of Contents

1. Introduction to Helm  
2. Helm Installation  
3. Helm Commands  
4. Helm Chart Structure  
5. Helm Lifecycle  
6. Helm Repositories  
7. Helm Hooks  
8. Helm with CI/CD  
9. Advanced Helm Concepts  
10. Helm Security  
11. Troubleshooting Helm  
12. References  

---

# 🚀 1. Introduction to Helm

## 🔹 What is Helm?

Helm is a package manager for Kubernetes that helps define, install, upgrade, and manage Kubernetes applications.

Helm uses:

- Charts
- Templates
- Releases

to simplify Kubernetes deployments.

---

## 🔑 Key Features of Helm

| Feature | Description |
|---|---|
| Kubernetes Package Manager | Simplifies application deployment |
| Helm Charts | Package Kubernetes manifests |
| Reusable Templates | Reuse Kubernetes configurations |
| Version Control | Manage release versions |
| Easy Rollbacks | Roll back failed deployments |
| CI/CD Friendly | Integrates with Jenkins, GitHub Actions, ArgoCD |

---

## 🔹 Important Helm Definitions

| Term | Definition |
|---|---|
| Chart | Collection of Kubernetes YAML files |
| Release | Running instance of a Helm chart |
| Repository | Location where charts are stored |
| values.yaml | File storing configurable values |
| Template | Dynamic Kubernetes YAML using Go templates |
| Helm Hook | Automated action during chart lifecycle |
| Subchart | Child chart inside parent chart |
| Helmfile | Declarative tool for managing multiple Helm releases |
| ChartMuseum | Helm chart repository server |

---

# 🛠️ 2. Helm Installation

## 🔹 Install Helm

```bash
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

---

## 🔹 Verify Helm Installation

```bash
helm version
```

---

## 🔹 Add Helm Repository

```bash
helm repo add stable https://charts.helm.sh/stable
```

---

## 🔹 Update Helm Repositories

```bash
helm repo update
```

---

# ⚙️ 3. Helm Commands

## 🔹 Install a Chart

```bash
helm install my-release stable/nginx
```

---

## 🔹 List Releases

```bash
helm list
```

---

## 🔹 Upgrade a Release

```bash
helm upgrade my-release stable/nginx
```

---

## 🔹 Uninstall a Release

```bash
helm uninstall my-release
```

---

## 🔹 Search Charts

```bash
helm search repo nginx
```

---

## 🔹 View Release Status

```bash
helm status my-release
```

---

## 🔹 Get Release Values

```bash
helm get values my-release
```

---

# 📦 4. Helm Chart Structure

## 🔹 Basic Chart Structure

```text
my-chart/
├── Chart.yaml
├── values.yaml
├── charts/
├── templates/
│   ├── deployment.yaml
│   ├── service.yaml
│   └── _helpers.tpl
```

---

## 🔹 Chart.yaml Example

```yaml
apiVersion: v2
name: my-chart
description: A Helm chart for Kubernetes
version: 0.1.0
```

---

## 🔹 values.yaml Example

```yaml
replicaCount: 3

image:
  repository: nginx
  tag: stable
```

---

## 🔹 Deployment Template Example

```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: {{ .Release.Name }}-nginx

spec:
  replicas: {{ .Values.replicaCount }}

  selector:
    matchLabels:
      app: {{ .Release.Name }}-nginx

  template:
    metadata:
      labels:
        app: {{ .Release.Name }}-nginx

    spec:
      containers:
      - name: nginx
        image: "{{ .Values.image.repository }}:{{ .Values.image.tag }}"
```

---

# 🔄 5. Helm Lifecycle

## 🔹 Create a New Chart

```bash
helm create my-chart
```

---

## 🔹 Render Templates Locally

```bash
helm template my-release my-chart
```

---

## 🔹 Lint a Chart

```bash
helm lint my-chart
```

---

## 🔹 Package a Chart

```bash
helm package my-chart
```

---

## 🔹 Install Local Chart

```bash
helm install my-release ./my-chart
```

---

# 📚 6. Helm Repositories

## 🔹 Create Local Repository Index

```bash
helm repo index ./charts --url http://example.com/charts
```

---

## 🔹 Serve Helm Charts

```bash
helm serve --address 0.0.0.0:8879
```

---

## 🔹 Add Custom Repository

```bash
helm repo add myrepo http://example.com/charts
```

---

## 🔹 Remove Repository

```bash
helm repo remove myrepo
```

---

# 🪝 7. Helm Hooks

## 🔹 What are Helm Hooks?

Helm Hooks allow execution of Kubernetes resources during:

- Install
- Upgrade
- Rollback
- Delete

---

## 🔹 Pre-Install Hook Example

```yaml
apiVersion: batch/v1
kind: Job

metadata:
  name: "{{ .Release.Name }}-preinstall"

  annotations:
    "helm.sh/hook": pre-install

spec:
  template:
    spec:
      containers:
      - name: preinstall
        image: busybox
        command: ['sh', '-c', 'echo Hello Helm']

      restartPolicy: Never
```

---

# 🚀 8. Helm with CI/CD

## 🔹 Helm in Jenkins Pipeline

```groovy
pipeline {

  agent any

  stages {

    stage('Deploy') {

      steps {

        script {

          sh "helm upgrade --install my-release ./my-chart"

        }
      }
    }
  }
}
```

---

## 🔹 Common CI/CD Use Cases

Helm is used for:

- Kubernetes Deployments
- Application Upgrades
- Blue-Green Deployment
- Canary Releases
- Rollbacks

---

# ⚡ 9. Advanced Helm Concepts

## 🔹 Subcharts

Subcharts help package related Kubernetes resources together.

Used for:

- Database dependencies
- Shared services
- Modular deployments

---

## 🔹 ChartMuseum

ChartMuseum is a Helm repository server used to:

- Store Helm charts
- Share charts
- Manage versions

---

## 🔹 Helmfile

Helmfile provides declarative management of multiple Helm releases.

Useful for:

- Multi-environment deployments
- Infrastructure automation

---

## 🔹 Helm Diff Plugin

Used to preview changes before deployment.

```bash
helm diff upgrade my-release my-chart
```

---

# 🔐 10. Helm Security

## 🔹 Chart Signing

Sign Helm charts for integrity verification.

### Sign a Chart

```bash
helm package --sign --key <key> --keyring <keyring> my-chart
```

---

### Verify a Chart

```bash
helm verify my-chart-0.1.0.tgz
```

---

## 🔹 RBAC with Helm

Use Kubernetes RBAC to:

- Restrict access
- Control deployments
- Secure namespaces

---

## 🔹 Secure Secrets

Best practices:

- Use Kubernetes Secrets
- Avoid hardcoded passwords
- Use sealed-secrets or Vault

---

# 🛠️ 11. Troubleshooting Helm

## 🔹 Debug Chart Installation

```bash
helm install --debug --dry-run my-release ./my-chart
```

---

## 🔹 View Release History

```bash
helm history my-release
```

---

## 🔹 Rollback a Release

```bash
helm rollback my-release 1
```

---

## 🔹 Check Helm Status

```bash
helm status my-release
```

---

## 🔹 Common Issues

| Issue | Solution |
|---|---|
| YAML Errors | Validate YAML indentation |
| Template Errors | Use helm template for debugging |
| Failed Release | Check pod logs and events |
| Chart Dependency Errors | Run helm dependency update |
| Permission Issues | Verify Kubernetes RBAC |

---

# 📚 12. References

## 🔹 Official Documentation

- Helm Official Documentation
- Helm Charts Repository
- Helm GitHub Repository

---

## 🔹 Community Resources

- ArtifactHub
- Helm Best Practices Guide
- Kubernetes Documentation

---

# 🎯 Final Takeaway

Helm simplifies Kubernetes application management by providing:

- Reusable charts
- Easy upgrades
- Rollbacks
- Templating
- Version control

It helps DevOps teams:

- Automate deployments
- Standardize Kubernetes apps
- Improve scalability
- Simplify CI/CD workflows

---

<p align="center">

⎈ Helm Simplifies Kubernetes Deployments 🚀

</p>
