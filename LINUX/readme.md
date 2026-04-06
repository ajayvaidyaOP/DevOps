# 🐧 Linux Basics for Beginners

<b>🚀Beginner Friendly | 💻 DevOps Ready | 📚 Easy to Understand</b>
</p>

  <img src="https://img.shields.io/badge/Linux-Notes-blue">
  <img src="https://img.shields.io/badge/Level-Beginner-green">
  <img src="https://img.shields.io/badge/Focus-DevOps-orange">
</p>

---

## 📌 Operating System (OS)

An Operating System (OS) is system software that manages computer hardware and software resources and acts as an interface between the user and the hardware.

### ❓ Why OS is Needed?
- To run applications  
- To manage CPU, memory, and storage  
- To provide user interface (CLI/GUI)  

---

## 🐧 Linux

Linux is an open-source operating system based on Unix.  
It is widely used in servers, cloud, and DevOps.

### ❓ Why Linux is Important?
- Free and open source  
- Secure and stable  
- Lightweight  
- Widely used in servers and cloud  

### ⚙️ Where Linux is Used?
- Web servers  
- Cloud (AWS, Azure, GCP)  
- DevOps  
- Embedded systems  

---

## 📜 History of Linux

### 🔹 UNIX
- Developed in 1969 at Bell Labs  
- Created by Ken Thompson and Dennis Ritchie  

### 🔹 GNU Project
- Started in 1983 by Richard Stallman  
- Provided tools like GCC, Bash  
- No kernel  

### 🔹 Linux
- Created in 1991 by Linus Torvalds  
- Developed Linux Kernel  

> ⚡ Linux Operating System = Linux Kernel + GNU Tools  

---

## 🧠 Linux Architecture

Linux architecture is divided into 4 main components:
![Linux Architecture](images/linux-architecture-circle.png)

### 🔹 Components

**1. Hardware**  
Physical components like CPU, RAM, Disk. All operations happen here.

---

**2. Kernel**  
Core of the operating system that directly interacts with hardware.

**Functions:**
- Process Management  
- Memory Management  
- Device Management  
- File System Management  

👉 Acts as a bridge between software and hardware.

---

**3. Shell**  
Interface between user and kernel.

- Takes user commands  
- Sends them to kernel  

Examples: bash, sh, zsh  

---

**4. Applications (User Space)**  
Programs used by users like browser, editor, DevOps tools.

---

### 🔄 Flow

User → Application → Shell → Kernel → Hardware  

> ❗ User cannot directly interact with Kernel  

---

## ⚔️ Linux vs Windows

<p align="center">
  <img src="https://img.shields.io/badge/Linux-vs--Windows-blue">
</p>

| Feature | Linux 🐧 | Windows 🪟 |
|--------|--------|----------|
| Interface | CLI (Mostly) | GUI |
| Source Code | Open Source | Closed Source |
| Cost | Free | Paid |
| Security | More Secure | Less Secure |
| Performance | Lightweight | Heavy |
| Usage | Servers, DevOps | Personal Use |

> 💡 Most servers run on Linux.

---

## 📦 Linux Distributions

<p align="center">
  <img src="https://img.shields.io/badge/Popular-Distros-green">
</p>

- Ubuntu  
- RedHat  
- Debian  
- Fedora  
- Amazon Linux  
- Kali Linux  
- Linux Mint  
- SUSE  

> 💡 Each distro is built for different use cases.

---

## 💻 Basic Linux Commands

<p align="center">
  <img src="https://img.shields.io/badge/Commands-Basics-orange">
</p>

## linux basic commmand 
ls - lissting 


```bash
whoami      # show current user
pwd         # present working directory
ls          # list files and folders
cd          # change directory
cd ..       # move back

uname -a    # system info
top         # running processes
df -h       # disk usage
free -h     # memory usage
