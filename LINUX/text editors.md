# 📝 LINUX TEXT EDITORS

![Linux](https://img.shields.io/badge/Linux-Editors-blue)
![Level](https://img.shields.io/badge/Level-Beginner_to_Advanced-green)
![DevOps](https://img.shields.io/badge/DevOps-Important-orange)

> 📚 Complete Guide to Linux Editors (Zero to Advanced)  
> ⚡ Used to create, edit and manage files in Linux

---

## 📌 WHAT ARE TEXT EDITORS?

Text editors are tools used to **create, open, edit, and modify files** in Linux.

👉 These files can be:
- Configuration files  
- Script files  
- Code files  
- Log files  

👉 Example:
- Editing `/etc/passwd`
- Writing shell scripts

---

## ❓ WHY TEXT EDITORS IMPORTANT

- Required to edit **system configuration files**
- Used in **DevOps (scripts, configs)**
- Helps in **quick file editing in terminal**
- Essential for **server management**

👉 Without editors, you cannot manage Linux systems properly

---

## 🔍 TYPES OF EDITORS IN LINUX

### 🟢 1. Command Line Editors (CLI)

- nano  
- vi  
- vim  

👉 Used inside terminal  
👉 Most important for DevOps

---

### 🔵 2. GUI Editors

- gedit  
- kate  

👉 Used with graphical interface  
👉 Easy but not used in servers

---

## 🧠 MOST IMPORTANT EDITORS

- nano → beginner friendly  
- vi → default editor  
- vim → advanced editor  

---

## ✏️ NANO EDITOR (BEGINNER)

### 📌 WHAT

Nano is a **simple and easy text editor**

---

### ❓ WHY

- Easy to use  
- No learning curve  
- Best for beginners  

---

### 🔧 HOW TO USE

Open file:
`nano file.txt`

Basic shortcuts:
- Ctrl + O → Save  
- Ctrl + X → Exit  
- Ctrl + K → Cut line  
- Ctrl + U → Paste  

---

## ⚙️ VI EDITOR (INTERMEDIATE)

### 📌 WHAT

Vi is a **default editor available in all Linux systems**

---

### ❓ WHY

- Available everywhere  
- Lightweight  
- Works in all servers  

---

### 🔧 MODES IN VI

- Normal mode → default mode  
- Insert mode → typing mode  
- Command mode → save/exit  

---

### 🔧 HOW TO USE

Open file:
`vi file.txt`

Switch modes:
- i → insert mode  
- Esc → normal mode  

Save & Exit:
- :w → save  
- :q → quit  
- :wq → save & exit  

---

## 🚀 VIM EDITOR (ADVANCED)

### 📌 WHAT

Vim = **Vi Improved**

---

### ❓ WHY

- More powerful than vi  
- Supports plugins  
- Faster editing  
- Used by professionals  

---

### 🔧 HOW TO USE

Open file:
`vim file.txt`

Common commands:
- i → insert  
- Esc → normal  
- :wq → save & exit  
- dd → delete line  
- yy → copy line  
- p → paste  

---

## ⚡ VI vs VIM vs NANO

| Feature | nano | vi | vim |
|--------|------|----|-----|
| Easy to use | ✅ | ❌ | ❌ |
| Default | ❌ | ✅ | ❌ |
| Advanced features | ❌ | ❌ | ✅ |
| Best for | Beginners | Servers | Professionals |

---

## 🔄 REAL SCENARIO

👉 You need to edit config file:

Command:
`vi /etc/nginx/nginx.conf`

👉 Change config → save → restart service

---

## ⚠️ COMMON MISTAKES

- Forgetting to press Esc in vi  
- Not saving file  
- Using wrong mode in vi/vim  

---

## 🏆 GOLDEN RULES

- Learn vi/vim (must for DevOps)  
- Use nano for quick edits  
- Practice commands daily  

---

## 🎤 INTERVIEW QUESTIONS

- What are text editors in Linux?  
- Difference between vi and vim?  
- What are modes in vi?  
- Which editor is best and why?  

---

## 🧪 PRACTICE LAB

Create file:
`nano test.txt`

Edit using vi:
`vi test.txt`

Edit using vim:
`vim test.txt`

---

## 💡 QUICK COMMANDS

`nano file.txt`  
`vi file.txt`  
`vim file.txt`  
