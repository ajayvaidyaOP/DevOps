# ⚙️ Jenkins Cheatsheet

> 🚀 Complete Jenkins Guide for Beginners to Advanced Users  
> 🔄 Learn Jenkins Installation, Pipelines, Plugins, CI/CD Automation, Security & Best Practices

---

# 📚 Table of Contents

1. Introduction to Jenkins  
2. Jenkins Installation  
3. Jenkins Pipeline  
4. Common Jenkins Commands  
5. Useful Jenkins Plugins  
6. Jenkins Best Practices  
7. Jenkins Configuration  
8. Advanced Jenkins  
9. Troubleshooting Jenkins  
10. References  

---

# 🚀 1. Introduction to Jenkins

## 🔹 What is Jenkins?

Jenkins is an open-source automation server that helps automate parts of software development related to building, testing, and deploying applications.

It enables:

- Continuous Integration (CI)
- Continuous Delivery (CD)
- Automated Testing
- Automated Deployment

---

## 🔑 Key Features of Jenkins

| Feature | Description |
|---|---|
| Open Source | Free and community-driven automation server |
| CI/CD Automation | Automates build, test, and deployment |
| Pipeline as Code | Define pipelines using Jenkinsfile |
| Plugin Ecosystem | Supports 1000+ plugins |
| Distributed Builds | Run builds on multiple agents |
| Integration Support | Works with Git, Docker, Kubernetes, AWS, etc. |

---

## 🔹 Important Jenkins Definitions

| Term | Definition |
|---|---|
| Jenkins Master / Controller | Main Jenkins server that manages jobs, pipelines, users, and agents |
| Jenkins Agent / Node | Worker machine that executes Jenkins jobs |
| Job | A task or build process executed by Jenkins |
| Build | Execution instance of a Jenkins job |
| Pipeline | Automated workflow containing multiple stages |
| Jenkinsfile | File containing pipeline code written in Groovy |
| Stage | Logical phase in pipeline like Build, Test, Deploy |
| Step | Single task inside a stage |
| Workspace | Directory where Jenkins stores project files during builds |
| Executor | Slot used to run jobs concurrently |
| Plugin | Extension used to add features to Jenkins |
| Artifact | Output generated after build process |
| SCM | Source Code Management system like Git |
| Trigger | Event that starts Jenkins jobs automatically |
| Webhook | Mechanism used by GitHub/GitLab to notify Jenkins |

---

# 🛠️ 2. Jenkins Installation

## 🐳 Install Jenkins Using Docker

### Run Jenkins Container

```bash
docker run -d \
-p 8080:8080 \
-p 50000:50000 \
jenkins/jenkins:lts
```

---

## 🐧 Install Jenkins on Ubuntu/Debian

### Add Jenkins Repository

```bash
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
```

```bash
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```

---

### Install Jenkins

```bash
sudo apt update
sudo apt install jenkins
```

---

## 🐧 Install Jenkins on CentOS/RHEL

### Add Repository

```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo \
https://pkg.jenkins.io/redhat-stable/jenkins.repo
```

```bash
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
```

---

### Install Jenkins

```bash
sudo yum install jenkins
```

---

## 🌐 Access Jenkins

Open browser:

```text
http://localhost:8080
```

---

# 🔄 3. Jenkins Pipeline

## 🔹 What is Jenkins Pipeline?

A Jenkins Pipeline is a collection of automated steps that define the CI/CD workflow.

Pipelines help automate:

- Build
- Testing
- Deployment
- Monitoring

---

## 🔹 Types of Pipelines

| Pipeline Type | Description |
|---|---|
| Declarative Pipeline | Simple and structured pipeline syntax |
| Scripted Pipeline | Advanced Groovy-based flexible pipeline |

---

## 🔹 Declarative Pipeline

```groovy
pipeline {

    agent any

    environment {
        MY_VAR = "value"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'make'
            }
        }

        stage('Test') {
            steps {
                sh 'make test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'make deploy'
            }
        }
    }

    post {

        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed.'
        }
    }
}
```

---

## 🔹 Scripted Pipeline

```groovy
node {

    stage('Checkout') {
        checkout scm
    }

    stage('Build') {
        sh 'make'
    }

    stage('Test') {
        sh 'make test'
    }

    stage('Deploy') {
        sh 'make deploy'
    }
}
```

---

# ⚙️ 4. Common Jenkins Commands

## 🔹 Restart Jenkins

```bash
sudo systemctl restart jenkins
```

---

## 🔹 Jenkins CLI

```bash
java -jar jenkins-cli.jar \
-s http://localhost:8080/ list-jobs
```

---

## 🔹 Check Jenkins Status

```bash
sudo systemctl status jenkins
```

---

## 🔹 Start Jenkins

```bash
sudo systemctl start jenkins
```

---

## 🔹 Stop Jenkins

```bash
sudo systemctl stop jenkins
```

---

# 🔌 5. Useful Jenkins Plugins

## 🔹 Pipeline Plugins

| Plugin | Purpose |
|---|---|
| Pipeline | Pipeline as Code support |
| Blue Ocean | Modern UI for pipelines |
| Pipeline Stage View | Visualize pipeline stages |

---

## 🔹 Source Control Plugins

| Plugin | Purpose |
|---|---|
| Git | Git integration |
| GitHub Integration | GitHub webhook integration |
| BitBucket Integration | BitBucket support |

---

## 🔹 Build Tool Plugins

| Plugin | Purpose |
|---|---|
| Maven Integration | Maven build support |
| Gradle | Gradle build support |
| NodeJS | Node.js environment |

---

## 🔹 Testing Plugins

| Plugin | Purpose |
|---|---|
| JUnit | Test reporting |
| Cobertura | Code coverage |
| SonarQube Scanner | Code quality scanning |

---

## 🔹 Deployment Plugins

| Plugin | Purpose |
|---|---|
| Docker | Docker integration |
| Kubernetes | Kubernetes deployment |
| AWS | AWS integration |

---

# ✅ 6. Jenkins Best Practices

## 🔹 Pipeline as Code

Always use Jenkinsfile for:

- Version control
- Reusability
- Consistency

---

## 🔹 Use Parameters

```groovy
parameters {
    string(
        name: 'ENV',
        defaultValue: 'dev',
        description: 'Environment'
    )
}
```

---

## 🔹 Secure Jenkins

Best practices:

- Regularly update plugins
- Use HTTPS
- Enable RBAC
- Use strong authentication
- Restrict admin access

---

## 🔹 Backup Jenkins

Backup important data:

- Jenkins Home Directory
- Jobs
- Plugins
- Credentials

---

# ⚙️ 7. Jenkins Configuration

## 🔹 Manage Jenkins

Go to:

```text
Dashboard → Manage Jenkins
```

Used for:

- Global configuration
- Plugin management
- Security settings
- Tool configuration

---

## 🔹 Configure Global Tools

Configure:

- JDK
- Maven
- Gradle
- Git
- Docker

Inside:

```text
Manage Jenkins → Global Tool Configuration
```

---

## 🔹 Jenkinsfile Configuration

Pipeline configuration is stored inside repository:

```text
Jenkinsfile
```

---

# 🚀 8. Advanced Jenkins

## 🔹 Parallel Stages

```groovy
pipeline {

    agent any

    stages {

        stage('Parallel') {

            parallel {

                stage('Unit Tests') {
                    steps {
                        sh 'make test'
                    }
                }

                stage('Integration Tests') {
                    steps {
                        sh 'make integration-test'
                    }
                }
            }
        }
    }
}
```

---

## 🔹 Shared Libraries

Used to:

- Reuse common pipeline code
- Centralize CI/CD logic
- Standardize pipelines

---

## 🔹 Jenkins Agents

Agents are worker machines that execute jobs.

Types:

- Static Agents
- Dynamic Agents
- Docker Agents
- Kubernetes Agents

---

## 🔹 Jenkins with Docker

Common use cases:

- Build Docker images
- Run containerized builds
- Deploy containers

---

## 🔹 Jenkins with Kubernetes

Used for:

- Dynamic build agents
- CI/CD pipelines
- Scalable Jenkins infrastructure

---

# 🛠️ 9. Troubleshooting Jenkins

## 🔹 Jenkins Won't Start

### Check Logs

```bash
sudo tail -f /var/log/jenkins/jenkins.log
```

---

### Fix Permissions

```bash
sudo chown -R jenkins:jenkins /var/lib/jenkins
```

---

## 🔹 Pipeline Failure Handling

```groovy
pipeline {

    agent any

    stages {

        stage('Build') {

            steps {

                script {

                    try {

                        sh 'make build'

                    } catch (exc) {

                        echo 'Build failed!'
                        throw exc
                    }
                }
            }
        }
    }
}
```

---

## 🔹 Plugin Issues

### Clear Plugin Cache

```bash
rm -rf $JENKINS_HOME/plugins/*.jpi
rm -rf $JENKINS_HOME/plugins/*.hpi
```

---

### Restart Jenkins

```bash
sudo systemctl restart jenkins
```

---

## 🔹 Useful Debugging Commands

### View Running Jobs

```bash
sudo systemctl status jenkins
```

---

### View Console Logs

```text
Jenkins Dashboard → Job → Console Output
```

---

# 📚 10. References

## 🔹 Official Documentation

- Jenkins Official Documentation

---

## 🔹 Community Resources

- Jenkins GitHub Repository
- Jenkins Community
- Jenkins Plugin Index

---

# 🎯 Final Takeaway

Jenkins is one of the most powerful CI/CD automation tools used in DevOps.

It helps teams:

- Automate software delivery
- Improve deployment speed
- Reduce manual work
- Increase release reliability
- Implement CI/CD pipelines efficiently

---

<p align="center">

⚙️ Jenkins Automates CI/CD Pipelines Efficiently 🚀

</p>
