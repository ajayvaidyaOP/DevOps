# ☕ Maven Cheatsheet

> 🚀 Complete Apache Maven Guide for Beginners to Advanced Users  
> 📦 Learn Maven Build Automation, Dependency Management, Plugins, Lifecycle & CI/CD Integration

---

# 📚 Table of Contents

1. Introduction to Maven  
2. Maven Installation  
3. Maven Project Structure  
4. Maven Lifecycle  
5. Common Maven Commands  
6. Maven Dependencies  
7. Maven Plugins  
8. Maven Profiles  
9. Maven with Jenkins  
10. Advanced Maven Concepts  
11. Troubleshooting Maven  
12. References  

---

# 🚀 1. Introduction to Maven

## 🔹 What is Maven?

Apache Maven is an open-source build automation and project management tool mainly used for Java applications.

Maven helps developers:

- Build applications
- Manage dependencies
- Run tests
- Package applications
- Automate deployments

---

## 🔑 Key Features of Maven

| Feature | Description |
|---|---|
| Build Automation | Automates application build process |
| Dependency Management | Automatically downloads required libraries |
| Standard Project Structure | Follows common directory layout |
| Plugin Support | Extends Maven functionality |
| Lifecycle Management | Automates project stages |
| CI/CD Integration | Works with Jenkins, GitHub Actions, GitLab CI |

---

## 🔹 Important Maven Definitions

| Term | Definition |
|---|---|
| POM | Project Object Model file (`pom.xml`) |
| Dependency | External library required by application |
| Repository | Storage location for dependencies |
| Plugin | Tool used to extend Maven features |
| Artifact | Output generated after build |
| Goal | Specific Maven task |
| Phase | Stage in Maven lifecycle |
| Build Lifecycle | Sequence of build phases |
| SNAPSHOT | Development version of application |
| Central Repository | Default Maven dependency repository |

---

# 🛠️ 2. Maven Installation

## 🔹 Install Java

Check Java installation:

```bash
java -version
```

---

## 🔹 Install Maven on Linux

```bash
sudo apt update
sudo apt install maven -y
```

---

## 🔹 Verify Maven Installation

```bash
mvn -version
```

---

## 🔹 Install Maven Manually

### Download Maven

```bash
wget https://downloads.apache.org/maven/maven-3/
```

---

### Extract Maven

```bash
tar -xvf apache-maven-*.tar.gz
```

---

### Set Environment Variables

```bash
export MAVEN_HOME=/opt/maven
export PATH=$MAVEN_HOME/bin:$PATH
```

---

# 📁 3. Maven Project Structure

## 🔹 Standard Maven Directory Structure

```text
my-app/
├── pom.xml
├── src/
│   ├── main/
│   │   ├── java/
│   │   └── resources/
│   └── test/
│       ├── java/
│       └── resources/
└── target/
```

---

## 🔹 Important Files and Directories

| File/Folder | Purpose |
|---|---|
| pom.xml | Maven project configuration |
| src/main/java | Application source code |
| src/test/java | Test source code |
| target/ | Generated build files |
| resources/ | Static configuration files |

---

## 🔹 Basic pom.xml Example

```xml
<project>

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>

    <artifactId>my-app</artifactId>

    <version>1.0</version>

    <dependencies>

        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.13.2</version>
        </dependency>

    </dependencies>

</project>
```

---

# 🔄 4. Maven Lifecycle

## 🔹 What is Maven Lifecycle?

Maven lifecycle is a sequence of phases used to build and manage projects.

---

## 🔹 Default Maven Lifecycle

| Phase | Purpose |
|---|---|
| validate | Validate project |
| compile | Compile source code |
| test | Run unit tests |
| package | Create JAR/WAR |
| verify | Run validations |
| install | Install package locally |
| deploy | Deploy artifact to remote repository |

---

## 🔹 Maven Lifecycle Flow

```text
validate → compile → test → package → verify → install → deploy
```

---

# ⚙️ 5. Common Maven Commands

## 🔹 Compile Project

```bash
mvn compile
```

---

## 🔹 Run Tests

```bash
mvn test
```

---

## 🔹 Package Application

```bash
mvn package
```

---

## 🔹 Install Dependency Locally

```bash
mvn install
```

---

## 🔹 Clean Build Files

```bash
mvn clean
```

---

## 🔹 Clean and Package

```bash
mvn clean package
```

---

## 🔹 Deploy Artifact

```bash
mvn deploy
```

---

## 🔹 Skip Tests

```bash
mvn package -DskipTests
```

---

## 🔹 Download Dependencies

```bash
mvn dependency:resolve
```

---

## 🔹 View Dependency Tree

```bash
mvn dependency:tree
```

---

# 📦 6. Maven Dependencies

## 🔹 What are Dependencies?

Dependencies are external libraries required by the application.

Example:

- Spring Boot
- JUnit
- Hibernate

---

## 🔹 Add Dependency Example

```xml
<dependency>

    <groupId>org.springframework.boot</groupId>

    <artifactId>spring-boot-starter-web</artifactId>

    <version>3.2.0</version>

</dependency>
```

---

## 🔹 Dependency Scopes

| Scope | Description |
|---|---|
| compile | Available everywhere |
| provided | Provided by runtime/server |
| runtime | Needed during runtime |
| test | Used only for testing |
| system | Local system dependency |

---

## 🔹 Maven Repositories

| Repository | Purpose |
|---|---|
| Local Repository | Stored in local machine |
| Central Repository | Default Maven repository |
| Remote Repository | Organization/private repository |

---

# 🔌 7. Maven Plugins

## 🔹 What are Maven Plugins?

Plugins extend Maven functionality.

Used for:

- Compilation
- Testing
- Packaging
- Deployment

---

## 🔹 Common Maven Plugins

| Plugin | Purpose |
|---|---|
| Compiler Plugin | Compile Java code |
| Surefire Plugin | Run unit tests |
| Jar Plugin | Create JAR files |
| War Plugin | Create WAR files |
| Shade Plugin | Build fat JAR |
| Checkstyle Plugin | Code quality checks |

---

## 🔹 Compiler Plugin Example

```xml
<plugin>

    <groupId>org.apache.maven.plugins</groupId>

    <artifactId>maven-compiler-plugin</artifactId>

    <version>3.11.0</version>

</plugin>
```

---

# ⚡ 8. Maven Profiles

## 🔹 What are Maven Profiles?

Profiles allow environment-specific configurations.

Examples:

- Dev
- QA
- Production

---

## 🔹 Profile Example

```xml
<profiles>

    <profile>

        <id>dev</id>

        <properties>
            <env>development</env>
        </properties>

    </profile>

</profiles>
```

---

## 🔹 Activate Profile

```bash
mvn package -Pdev
```

---

# 🚀 9. Maven with Jenkins

## 🔹 Maven Build in Jenkins Pipeline

```groovy
pipeline {

    agent any

    stages {

        stage('Build') {

            steps {

                sh 'mvn clean package'

            }
        }
    }
}
```

---

## 🔹 Common CI/CD Usage

Maven is commonly used for:

- Java Builds
- Unit Testing
- Artifact Packaging
- SonarQube Scanning
- Docker Builds

---

# ⚡ 10. Advanced Maven Concepts

## 🔹 Multi-Module Projects

Used to manage multiple related projects together.

Example:

```text
parent-project/
├── module-1/
├── module-2/
└── pom.xml
```

---

## 🔹 Maven Wrapper

Maven Wrapper ensures consistent Maven version.

```bash
./mvnw clean package
```

---

## 🔹 SNAPSHOT Versions

SNAPSHOT indicates development versions.

Example:

```text
1.0-SNAPSHOT
```

---

## 🔹 Effective POM

Displays final merged POM configuration.

```bash
mvn help:effective-pom
```

---

# 🛠️ 11. Troubleshooting Maven

## 🔹 Common Issues

| Issue | Solution |
|---|---|
| Dependency Not Found | Check repository and internet |
| Build Failure | Check logs and syntax |
| Java Version Error | Verify JAVA_HOME |
| Plugin Failure | Update plugin version |
| Test Failures | Review test cases |

---

## 🔹 Debug Maven Build

```bash
mvn clean install -X
```

---

## 🔹 Skip Test Failures

```bash
mvn install -Dmaven.test.failure.ignore=true
```

---

## 🔹 Clean Local Repository Cache

```bash
rm -rf ~/.m2/repository
```

---

# 📚 12. References

## 🔹 Official Documentation

- Apache Maven Official Documentation
- Maven Central Repository
- Maven Plugin Documentation

---

## 🔹 Community Resources

- Baeldung Maven Tutorials
- Maven GitHub Repository
- Spring Boot Maven Guide

---

# 🎯 Final Takeaway

Maven is one of the most popular build tools in the Java ecosystem.

It helps developers:

- Automate builds
- Manage dependencies
- Standardize project structure
- Integrate CI/CD pipelines
- Simplify Java application deployment

---

<p align="center">

☕ Maven Simplifies Java Build Automation 🚀

</p>
