# 🌐 LINUX NETWORKING

![Linux](https://img.shields.io/badge/Linux-Networking-blue)
![Level](https://img.shields.io/badge/Level-Beginner_to_Advanced-green)
![DevOps](https://img.shields.io/badge/DevOps-Core-orange)

> 📚 Complete Guide to Linux Networking  
> ⚡ Used to connect systems, communicate, and manage network operations

---

## 📌 WHAT IS NETWORKING?

Networking is the process of **connecting systems to communicate with each other**

👉 Example:
- Accessing websites  
- Connecting to servers  
- Data transfer between machines  

---

## ❓ WHY NETWORKING IMPORTANT

- Required for internet access  
- Used in servers & cloud  
- Enables communication between systems  
- Essential for DevOps  

---

## 🌍 BASIC NETWORK TERMS

- IP Address → unique identity of system  
- Gateway → route to external network  
- DNS → converts domain to IP  
- Port → communication endpoint  

---

## 🔍 CHECK NETWORK

Command: `ip a`

👉 Shows IP address and interfaces  

---

## 🌐 CHECK CONNECTIVITY

Ping command:
`ping google.com`

👉 Tests network connection  

---

## 🔎 DNS LOOKUP

Command:
`nslookup google.com`

---

## 📡 CHECK ROUTING

Command:
`ip route`

---

## 🧾 NETWORK CONFIG FILE

Path:
`/etc/sysconfig/network-scripts/`

👉 Stores network configuration (RHEL based)

---

## 🔧 NETWORK COMMANDS

Check IP:
`ip a`

Check routing:
`ip route`

Check DNS:
`cat /etc/resolv.conf`

---

## 🔌 CHECK PORTS

Command:
`netstat -tulnp`

Alternative:
`ss -tulnp`

---

## 📡 DOWNLOAD / TEST NETWORK

Using curl:
`curl google.com`

Using wget:
`wget http://example.com`

---

## 🔄 RESTART NETWORK

Command:
`systemctl restart network`

---

## 🔗 SSH (REMOTE ACCESS)

Connect:
`ssh user@ip`

👉 Used to access remote server  

---

## ⚡ FIREWALL BASICS

Check status:
`systemctl status firewalld`

Allow port:
`firewall-cmd --add-port=80/tcp --permanent`

Reload:
`firewall-cmd --reload`

---

## 🔄 REAL SCENARIO

👉 Server not reachable:

Steps:
1. `ping`  
2. `ip a`  
3. `ip route`  
4. `ss -tulnp`  

---

## ⚠️ COMMON MISTAKES

- Wrong IP configuration  
- DNS issue  
- Firewall blocking port  

---

## 🔒 SECURITY TIP

- Open only required ports  
- Use SSH keys  
- Disable unused services  

---

## 🏆 GOLDEN RULES

- Always check IP first  
- Use ping for testing  
- Verify ports and firewall  

---

## 🎤 INTERVIEW QUESTIONS

- What is IP address?  
- Difference between TCP and UDP?  
- What is DNS?  
- What is port?  

---

## 🧪 PRACTICE LAB

Check IP:
`ip a`

Ping:
`ping google.com`

Check ports:
`ss -tulnp`

SSH:
`ssh user@ip`

---

## 💡 QUICK COMMANDS

`ip a`  
`ping`  
`nslookup`  
`ip route`  
`ss -tulnp`  
`curl`  
`ssh`  
