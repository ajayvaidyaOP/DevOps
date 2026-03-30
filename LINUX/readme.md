# 🐧 Linux Notes for Beginners 🚀

![Linux](https://img.shields.io/badge/Linux-Notes-blue)
![Level](https://img.shields.io/badge/Level-Beginner-green)
![Focus](https://img.shields.io/badge/Focus-DevOps-orange)

---

## 📌 Introduction

Linux is an **open-source operating system** that manages hardware and software resources.  
It acts as an interface between the **user and hardware**.

> ⚠️ Linux is widely used in servers, cloud, and DevOps.

---

## ⚙️ What is Operating System?

An Operating System (OS) is system software that:
- Manages hardware resources  
- Manages software applications  
- Provides interface between user and system  

---

## ⚔️ Linux vs Windows

| Feature          | Linux 🐧                     | Windows 🪟                  |
|-----------------|----------------------------|----------------------------|
| Interface       | CLI                        | GUI                        |
| Usability       | Difficult                  | Easy                       |
| Source Code     | Open Source                | Closed Source              |
| Licensing       | Free                       | Paid                       |
| Resource Usage  | Lightweight                | Heavy                      |
| Security        | More Secure                | Less Secure                |

---

## 🧩 Types of Operating Systems

- **Batch OS** – Executes jobs in batches  
- **Time-Sharing OS** – Multiple users at same time  
- **Distributed OS** – Multiple systems work as one  
- **Embedded OS** – Used in smart devices  
- **Real-Time OS** – Immediate response systems  
- **Network OS** – Used for networking  
- **Mobile OS** – Used in smartphones  

---

## 🖧 What is a Server?

A server is a system that provides services or resources to other systems (clients) over a network.

**Examples:**
- Web Server  
- File Server  
- Database Server  

---

## 🖥️ Desktop OS vs Server OS

| Feature     | Desktop OS                  | Server OS                     |
|------------|----------------------------|-------------------------------|
| Purpose    | Personal use               | Network management            |
| Users      | Single user                | Multiple users                |
| Performance| UI focused                 | High performance              |
| Uptime     | Can restart               | 24/7 required                 |
| Interface  | GUI                        | CLI preferred                 |
| Security   | Basic                      | Advanced                      |

---

## 🧠 Linux Architecture

Linux has 4 main components:

- **Hardware** – CPU, RAM, Disk  
- **Kernel** – Core of OS (talks to hardware)  
- **Shell** – Interface between user & kernel  
- **Applications** – User programs  

### 📷 Architecture Diagram
![Linux Architecture](images/linux-architecture.png)

---

## 📦 Linux Distributions

- RedHat  
- Debian  
- Ubuntu  
- Fedora  
- Amazon Linux  
- Kali Linux  
- Linux Mint  
- SUSE  

---

## 💻 Basic Linux Commands

```bash
whoami              # Show current user
hostname            # Show hostname
pwd                 # Current directory
cat /etc/os-release # OS info
uname -a            # Kernel info
free -h             # Memory usage
df -h               # Disk usage
ls                  # List files
cd <dir>            # Change directory
cd ..               # Back
echo $SHELL         # Current shell
exit                # Exit terminal
top                 # Running processes
lscpu               # CPU info
lsblk               # Storage devices
du -sh <file/dir>   # Size of file/folder
