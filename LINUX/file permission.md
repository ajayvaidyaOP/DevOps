# 🔐 LINUX FILE PERMISSIONS

![Linux](https://img.shields.io/badge/Linux-Permissions-blue)
![Level](https://img.shields.io/badge/Level-Beginner-green)
![DevOps](https://img.shields.io/badge/DevOps-Ready-orange)

> 📚 Beginner Friendly Notes  
> ⚡ Permissions decide who can read, write, and execute files in Linux

---

## 📌 WHAT ARE FILE PERMISSIONS

File permissions control **who can access a file or directory** and **what actions they can perform**.

- Who can read the file  
- Who can modify the file  
- Who can execute the file  

👉 Helps in protecting data and preventing unauthorized access

---

## ❓ WHY FILE PERMISSIONS IMPORTANT

- Protect sensitive data  
- Prevent unauthorized access  
- Control modification & deletion  
- Improve system security  

---

## 🔍 HOW TO CHECK PERMISSIONS

Command: `ls -l`  

Example output:  
`-rwxr-xr-- 1 user group 123 May 10 file.txt`

---

## 🖥️ COMMAND + OUTPUT

Command: `ls -l`  
Output: `-rw-r--r-- 1 user group 0 May 10 demo.txt`

---

## 📊 UNDERSTANDING PERMISSION FORMAT

Example: `-rwxr-xr--`

- File type → -  
- Owner → rwx  
- Group → r-x  
- Others → r--  

Visual: `[ - ][ rwx ][ r-x ][ r-- ]`

---

## 📁 FILE TYPES IN LINUX

- `-` → Regular file (text, image, program file)  
- `d` → Directory (folder)  
- `l` → Link file (shortcut / symbolic link)  
- `b` → Block device (hard disk, storage devices)  
- `c` → Character device (keyboard, terminal)  
- `s` → Socket (communication between processes)  
- `p` → Pipe (used for process communication)  

👉 Example:
- `/etc/passwd` → regular file  
- `/home` → directory  

---

## ⚡ SHORTCUT TRICK

- rwx = 7  
- rw- = 6  
- r-x = 5  
- r-- = 4  

Example:  
- 755 = rwx r-x r-x  
- 644 = rw- r-- r--  

---

## 📊 PERMISSION TABLE

| Symbol | Meaning | Value |
|--------|--------|-------|
| r | Read | 4 |
| w | Write | 2 |
| x | Execute | 1 |

---

## 👤 OWNERSHIP

- Owner → creator  
- Group → group users  
- Others → remaining users  

---

## 🔧 CHANGE PERMISSIONS

Command: `chmod 755 file`

Breakdown:  
- 7 → Owner → rwx  
- 5 → Group → r-x  
- 5 → Others → r-x  

---

## 🔄 BEFORE VS AFTER

Before: `-rw-r--r--`  
After:  `-rwxr-xr-x`  

---

## 🧮 DEFAULT PERMISSIONS (UMASK)

Root user:  
- 777 - 022 = 755  
- 666 - 022 = 644  

Normal user:  
- 777 - 002 = 775  
- 666 - 002 = 664  

---

## ⚠️ COMMON MISTAKES

- Using 777  
- Missing execute permission  
- Wrong ownership  

---

## 🔒 SECURITY TIP

Avoid using 777 in production  
Follow least privilege principle  

---

## 🏆 GOLDEN RULES

- Give only required permissions  
- Avoid full access  
- Keep system secure  

---

## 🚀 REAL DEVOPS USE CASE

- 755 → scripts  
- 644 → config files  

---

## 🎤 INTERVIEW QUESTIONS

- What is file permission?  
- Difference between 644 and 755?  
- What are file types in Linux?  
- What is umask?  

---

## 💡 QUICK COMMANDS

`ls -l`  
`chmod 755 file`  
`chown user file`  
`chgrp group file`  
