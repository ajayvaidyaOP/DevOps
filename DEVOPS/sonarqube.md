# 🔍 SonarQube Cheatsheet

> 🚀 Complete SonarQube Guide for Beginners to Advanced Users  
> 🛡️ Learn Code Quality Analysis, Security Scanning, CI/CD Integration & Best Practices

---

# 📚 Table of Contents

1. Introduction to SonarQube  
2. SonarQube Installation  
3. Configuring SonarQube  
4. Running Code Analysis  
5. SonarQube Plugins  
6. Advanced SonarQube Features  
7. Managing Users & Permissions  
8. Monitoring & Reporting  
9. Scaling SonarQube  
10. Troubleshooting SonarQube  
11. References  

---

# 🚀 1. Introduction to SonarQube

## 🔹 What is SonarQube?

SonarQube is an open-source platform used for continuous inspection of code quality.

It performs static code analysis to detect:

- Bugs
- Security Vulnerabilities
- Code Smells
- Duplicated Code
- Poor Coding Practices

It integrates with CI/CD tools like:

- Jenkins
- GitHub Actions
- GitLab CI/CD
- Azure DevOps

---

## 🔑 Key Features of SonarQube

| Feature | Description |
|---|---|
| Static Code Analysis | Analyze source code automatically |
| Security Scanning | Detect vulnerabilities and risks |
| Quality Gates | Prevent bad-quality code deployment |
| CI/CD Integration | Integrates with Jenkins, GitHub, GitLab |
| Multi-language Support | Supports Java, Python, JS, Go, etc. |
| Reporting Dashboard | Detailed project quality metrics |

---

## 🔹 Important SonarQube Definitions

| Term | Definition |
|---|---|
| SonarQube Server | Main platform that processes analysis reports |
| Sonar Scanner | Tool used to scan source code |
| Quality Gate | Set of conditions defining code quality |
| Quality Profile | Collection of analysis rules |
| Code Smell | Maintainability issue in code |
| Bug | Logic issue causing incorrect behavior |
| Vulnerability | Security weakness in application |
| Technical Debt | Future maintenance effort caused by poor code |
| Coverage | Percentage of tested code |
| Duplication | Repeated blocks of code |
| Issue | Problem detected during analysis |
| Rule | Condition used for static analysis |

---

# 🛠️ 2. SonarQube Installation

## 🐳 Install SonarQube Using Docker

### Run SonarQube Container

```bash
docker run -d \
--name sonarqube \
-p 9000:9000 \
sonarqube
```

---

## 🐧 Manual Installation on Linux

### Download SonarQube

```bash
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-8.9.0.43852.zip
```

---

### Extract Files

```bash
unzip sonarqube-8.9.0.43852.zip
```

---

### Start SonarQube

```bash
cd sonarqube-8.9.0.43852/bin/linux-x86-64
./sonar.sh start
```

---

## 🌐 Access SonarQube

Open browser:

```text
http://localhost:9000
```

Default credentials:

```text
Username: admin
Password: admin
```

---

# ⚙️ 3. Configuring SonarQube

## 🔹 Database Configuration

SonarQube requires databases like:

- PostgreSQL
- MySQL
- Oracle

---

## 🔹 Configure Database Connection

Edit:

```text
sonar.properties
```

Add:

```properties
sonar.jdbc.url=jdbc:postgresql://localhost/sonarqube
sonar.jdbc.username=sonar
sonar.jdbc.password=sonar
```

---

## 🔹 Quality Profiles

Quality Profiles define coding rules used during analysis.

Used for:

- Security standards
- Coding conventions
- Best practices

Manage from:

```text
SonarQube Dashboard → Quality Profiles
```

---

# 🔍 4. Running Code Analysis

## 🔹 Install Sonar Scanner

```bash
npm install -g sonarqube-scanner
```

---

## 🔹 Run SonarQube Scan

```bash
sonar-scanner \
-Dsonar.projectKey=my-project \
-Dsonar.sources=. \
-Dsonar.host.url=http://localhost:9000 \
-Dsonar.login=admin \
-Dsonar.password=admin
```

---

## 🔹 CI/CD Integration

SonarQube integrates with:

- Jenkins
- GitHub Actions
- GitLab CI/CD
- Azure DevOps

Used for:

- Automated code scanning
- Security checks
- Quality enforcement

---

# 🔌 5. SonarQube Plugins

## 🔹 Installing Plugins

Go to:

```text
Administration → Marketplace
```

Search and install plugins.

---

## 🔹 Popular Plugins

| Plugin | Purpose |
|---|---|
| SonarLint | IDE integration |
| SonarCSS | CSS code analysis |
| SonarTS | TypeScript analysis |
| FindBugs | Java bug detection |
| Checkstyle | Coding standards enforcement |

---

## 🔹 SonarLint IDE Integration

Supports IDEs like:

- VS Code
- IntelliJ IDEA
- Eclipse

Provides:

- Real-time code analysis
- Bug detection while coding

---

# 🚀 6. Advanced SonarQube Features

## 🔹 Code Coverage

Integrates with tools like:

- Jacoco
- Istanbul
- Cobertura

Used to measure:

- Tested code percentage
- Unit test quality

---

## 🔹 Security Vulnerability Detection

SonarQube detects:

- SQL Injection
- XSS
- Hardcoded Secrets
- Unsafe APIs

Based on standards like:

- OWASP
- SANS

---

## 🔹 Quality Gates

Quality Gates help block deployments if:

- Coverage is low
- Bugs exist
- Vulnerabilities are detected

---

# 👥 7. Managing Users & Permissions

## 🔹 User Management

Manage users from:

```text
Administration → Security → Users
```

---

## 🔹 Roles

| Role | Access |
|---|---|
| Admin | Full control |
| User | Basic access |
| Code Viewer | View analysis reports |

---

## 🔹 LDAP / SSO Integration

Configure centralized authentication using:

- LDAP
- SAML
- OAuth
- Active Directory

---

# 📊 8. Monitoring & Reporting

## 🔹 Project Dashboards

Dashboards display:

- Code Coverage
- Vulnerabilities
- Technical Debt
- Duplications
- Bugs

---

## 🔹 Custom Reports

Generate reports for:

- Management
- Compliance
- Audits
- Team Reviews

---

# ⚡ 9. Scaling SonarQube

## 🔹 High Availability

Large deployments can use:

- Multiple nodes
- Load balancers
- Dedicated databases

---

## 🔹 Performance Optimization

Best practices:

- Allocate enough RAM
- Use PostgreSQL
- Separate database server
- Optimize JVM settings

---

# 🛠️ 10. Troubleshooting SonarQube

## 🔹 Out Of Memory Issues

Increase JVM Heap Size.

Edit:

```text
sonar.properties
```

---

## 🔹 Enable Debug Logging

```properties
sonar.log.level=DEBUG
```

---

## 🔹 Failed Scans

Check logs inside:

```text
logs/
```

---

## 🔹 Verify SonarQube Status

```bash
ps -ef | grep sonar
```

---

## 🔹 Restart SonarQube

```bash
./sonar.sh restart
```

---

# 📚 11. References

## 🔹 Official Resources

- SonarQube Documentation
- Sonar Scanner Documentation
- SonarLint Documentation

---

## 🔹 Community Resources

- SonarQube GitHub Repository
- Sonar Community Forum
- OWASP Security Guidelines

---

# 🎯 Final Takeaway

SonarQube is one of the most powerful tools for maintaining:

- Code Quality
- Security Standards
- Clean Architecture
- CI/CD Validation

It helps teams:

- Detect issues early
- Improve maintainability
- Reduce technical debt
- Secure applications
- Automate code reviews

---

<p align="center">

🔍 SonarQube Improves Code Quality & Security 🚀

</p>
