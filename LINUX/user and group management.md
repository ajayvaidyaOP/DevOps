# 👥 LINUX USER & GROUP MANAGEMENT

![Linux](https://img.shields.io/badge/Linux-Users_&_Groups-blue)
![Level](https://img.shields.io/badge/Level-Beginner_to_Advanced-green)
![DevOps](https://img.shields.io/badge/DevOps-Core-orange)

> 📚 Complete Guide to Linux Users & Groups  
> ⚡ Used to manage access, permissions, and security in Linux

---

## 📌 WHAT IS USER MANAGEMENT

User management is the process of **creating and managing users** in Linux.

---

## ❓ WHY USER MANAGEMENT IMPORTANT

- Controls system access  
- Improves security  
- Supports multi-user environment  

---

## 👤 TYPES OF USERS

- Root User → full access  
- Normal User → limited access  
- System User → service users  

---

## 🔍 CHECK USERS

Command: `cat /etc/passwd`

---

## 🔧 USER MANAGEMENT COMMANDS

Create user:  
`useradd username`

Set password:  
`passwd username`

Modify user:  
`usermod username`

Delete user:  
`userdel username`

---

## 📄 /etc/passwd FILE

👉 Stores basic user information

Example:  
`user:x:1001:1001:/home/user:/bin/bash`

Breakdown:

- Username  
- Password (x placeholder)  
- UID  
- GID  
- Home directory  
- Shell  

👉 Password yaha store nahi hota (security reason)

---

## 🔐 /etc/shadow FILE

👉 Stores encrypted passwords

Command to view:  
`sudo cat /etc/shadow`

Example:  
`user:$6$abc123$hashvalue:19000:0:99999:7:::`

Breakdown:

- Username  
- Encrypted password  
- Last password change  
- Minimum days  
- Maximum days  
- Warning days  
- Inactive days  
- Expiry  

👉 Only root can access this file

---

## 📌 WHAT IS GROUP MANAGEMENT

Group management is used to manage multiple users together

---

## ❓ WHY GROUPS IMPORTANT

- Easy permission handling  
- Better control  
- Used in teams  

---

## 🔍 CHECK GROUPS

Command: `cat /etc/group`

---

## 🔧 GROUP COMMANDS

Create group:  
`groupadd groupname`

Add user to group:  
`usermod -aG group user`

Delete group:  
`groupdel groupname`

---

## 📄 /etc/group FILE

👉 Stores group information

Example:  
`devops:x:1002:ajay,user1`

Breakdown:

- Group name  
- Password (x)  
- GID  
- Members  

---

## 🔐 /etc/gshadow FILE

👉 Secure version of group file

Command to view:  
`sudo cat /etc/gshadow`

Example:  
`devops:!:admin:ajay,user1`

Breakdown:

- Group name  
- Encrypted password  
- Group admin  
- Members  

---

## 🔁 FILE COMPARISON

| File | Purpose |
|------|--------|
| /etc/passwd | User info |
| /etc/shadow | Password |
| /etc/group | Group info |
| /etc/gshadow | Secure group |

---

## ⚡ IMPORTANT IDS

- UID → User ID  
- GID → Group ID  
👉 Root UID = 0  

---

## 🔗 USER & GROUP RELATION

- One primary group  
- Multiple secondary groups  

---

## 🔄 REAL SCENARIO

`useradd dev1`  
`passwd dev1`  
`groupadd developers`  
`usermod -aG developers dev1`  

---

## ⚠️ COMMON MISTAKES

- Not setting password  
- Not adding user to group  
- Wrong permissions  

---

## 🔒 SECURITY TIP

- Never share root access  
- Follow least privilege  

---

## 🏆 GOLDEN RULES

- Use groups for management  
- Keep system secure  
- Limit access  

---

## 🎤 INTERVIEW QUESTIONS

- What is /etc/passwd?  
- Where password stored?  
- Difference passwd vs shadow?  
- What is UID/GID?  

---

## 🧪 PRACTICE LAB

`useradd testuser`  
`passwd testuser`  
`groupadd dev`  
`usermod -aG dev testuser`  
`id testuser`  

---

## 💡 QUICK COMMANDS

`useradd user`  
`passwd user`  
`userdel user`  
`groupadd group`  
`usermod -aG group user`  
`id user`  
