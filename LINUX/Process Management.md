# ⚙️ LINUX PROCESS MANAGEMENT

![Linux](https://img.shields.io/badge/Linux-Process_Management-blue)
![Level](https://img.shields.io/badge/Level-Beginner_to_Advanced-green)
![DevOps](https://img.shields.io/badge/DevOps-Core-orange)

> 📚 Complete Guide to Linux Processes  
> ⚡ Used to manage running programs and system tasks

---

## 📌 WHAT IS A PROCESS?

A process is a **running instance of a program** in Linux.

👉 Example:
- Running `nginx`
- Running `java application`

---

## ❓ WHY PROCESS MANAGEMENT IMPORTANT

- Monitor system performance  
- Control running programs  
- Kill unwanted processes  
- Essential in servers & DevOps  

---

## 🔍 HOW TO CHECK PROCESSES

Command: `ps`

Common usage:
- `ps -ef` → show all processes  
- `ps aux` → detailed view  

---

## 📊 PROCESS INFORMATION

Example:
`root  1234  1  0 10:00 ? 00:00:01 nginx`

Breakdown:

- User  
- PID (Process ID)  
- PPID (Parent Process ID)  
- CPU usage  
- Time  
- Command  

---

## 🧾 REAL-TIME MONITORING

Command: `top`

👉 Shows live processes  
👉 Press `q` to exit  

Alternative:
`htop` (better UI)

---

## 🔍 SEARCH PROCESS

Command:  
`ps aux | grep process_name`

Example:
`ps aux | grep nginx`

---

## ⚡ PROCESS STATES

- R → Running  
- S → Sleeping  
- T → Stopped  
- Z → Zombie  

---

## 🔧 CONTROL PROCESSES

Kill process:
`kill PID`

Force kill:
`kill -9 PID`

Kill by name:
`pkill process_name`

---

## 🔄 BACKGROUND & FOREGROUND

Run in background:
`command &`

Bring to foreground:
`fg`

List jobs:
`jobs`

---

## ⏸️ STOP & RESUME PROCESS

Stop:
`Ctrl + Z`

Resume in background:
`bg`

Resume in foreground:
`fg`

---

## ⏱️ PROCESS PRIORITY

Nice value range:
-20 → highest priority  
+19 → lowest priority  

Check:
`nice`

Set priority:
`nice -n 10 command`

Change running process:
`renice 10 PID`

---

## 🔗 PARENT & CHILD PROCESS

- Parent process → creates other processes  
- Child process → created by parent  

👉 Example:
Shell → runs command → creates process  

---

## 🔄 REAL SCENARIO

👉 Application consuming high CPU:

Steps:
1. `top`  
2. Find PID  
3. `kill PID`  

---

## ⚠️ COMMON MISTAKES

- Killing wrong process  
- Using `kill -9` unnecessarily  
- Not checking PID properly  

---

## 🔒 SECURITY TIP

- Do not kill system processes  
- Always verify process before killing  

---

## 🏆 GOLDEN RULES

- Use `top` for monitoring  
- Use `kill` carefully  
- Understand process before action  

---

## 🎤 INTERVIEW QUESTIONS

- What is a process?  
- Difference between PID and PPID?  
- What is zombie process?  
- Difference between kill and kill -9?  

---

## 🧪 PRACTICE LAB

Run process:
`sleep 100`

Check:
`ps`

Kill:
`kill PID`

Run background:
`sleep 200 &`

Check jobs:
`jobs`

---

## 💡 QUICK COMMANDS

`ps -ef`  
`top`  
`kill PID`  
`kill -9 PID`  
`jobs`  
`bg`  
`fg`  
