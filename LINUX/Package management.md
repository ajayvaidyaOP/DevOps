# 📦 LINUX PACKAGE MANAGEMENT

![Linux](https://img.shields.io/badge/Linux-Package_Management-blue)
![Level](https://img.shields.io/badge/Level-Beginner_to_Advanced-green)
![DevOps](https://img.shields.io/badge/DevOps-Core-orange)

> 📚 Complete Guide to Package Management in Linux  
> ⚡ Used to install, update, remove and manage software

---

## 📌 WHAT IS PACKAGE MANAGEMENT

Package management is the process of **installing, updating, and removing software** in Linux.

👉 Software in Linux is called a **package**

---

## ❓ WHY PACKAGE MANAGEMENT IMPORTANT

- Easy software installation  
- Automatic dependency handling  
- Keeps system updated  
- Essential for servers & DevOps  

---

## 📦 TYPES OF PACKAGE MANAGERS

### 🔴 RPM (RedHat Based)

- Used in RHEL, CentOS, Amazon Linux  
- Package format → `.rpm`

---

### 🔵 APT (Debian Based)

- Used in Ubuntu, Debian  
- Package format → `.deb`

---

## 🔍 CHECK INSTALLED PACKAGES

RPM:
`rpm -qa`

APT:
`dpkg -l`

---

## 🔧 INSTALL PACKAGE

RPM (manual):
`rpm -ivh package.rpm`

YUM (recommended):
`yum install package`

DNF (latest):
`dnf install package`

APT:
`apt install package`

---

## ❌ REMOVE PACKAGE

YUM:
`yum remove package`

DNF:
`dnf remove package`

APT:
`apt remove package`

---

## 🔄 UPDATE PACKAGE

Update single package:
`yum update package`

Update all:
`yum update`

DNF:
`dnf update`

APT:
`apt update && apt upgrade`

---

## 🔍 SEARCH PACKAGE

YUM:
`yum search package`

DNF:
`dnf search package`

APT:
`apt search package`

---

## 📦 PACKAGE INFO

RPM:
`rpm -qi package`

APT:
`apt show package`

---

## 🔗 DEPENDENCIES

👉 Some packages need other packages to work

Example:
Installing nginx → installs required libraries

👉 YUM / DNF / APT handle dependencies automatically

---

## 📁 REPOSITORIES

👉 Repository = location where packages are stored

Check repos:
`yum repolist`

APT:
`cat /etc/apt/sources.list`

---

## 🔄 REAL SCENARIO

👉 Install nginx:

`yum install nginx`

Start service:
`systemctl start nginx`

---

## ⚠️ COMMON MISTAKES

- Using rpm without dependencies  
- Not updating repo  
- Installing wrong package  

---

## 🔒 SECURITY TIP

- Install from trusted repositories  
- Keep system updated  

---

## 🏆 GOLDEN RULES

- Prefer yum/dnf over rpm  
- Always update before install  
- Check dependencies  

---

## 🎤 INTERVIEW QUESTIONS

- What is package manager?  
- Difference between rpm and yum?  
- What is repository?  
- What is dependency?  

---

## 🧪 PRACTICE LAB

Search package:
`yum search nginx`

Install:
`yum install nginx`

Check:
`rpm -qa | grep nginx`

Remove:
`yum remove nginx`

---

## 💡 QUICK COMMANDS

`yum install package`  
`yum remove package`  
`yum update`  
`rpm -qa`  
`dnf install package`  
`apt install package`  
