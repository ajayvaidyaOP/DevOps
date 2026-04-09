# 📦 LINUX ARCHIVE & COMPRESSION

![Linux](https://img.shields.io/badge/Linux-Archive_&_Compression-blue)
![Level](https://img.shields.io/badge/Level-Beginner_to_Advanced-green)
![DevOps](https://img.shields.io/badge/DevOps-Core-orange)

> 📚 Complete Guide to Archiving & Compression in Linux  
> ⚡ Used to combine files and reduce file size

---

## 📌 WHAT IS ARCHIVING?

Archiving means **combining multiple files into a single file**

👉 Example:
- Multiple files → one `.tar` file  

👉 Archiving does NOT reduce file size

---

## 📌 WHAT IS COMPRESSION?

Compression means **reducing file size**

👉 Example:
- `file.txt` → `file.txt.gz`  

👉 Helps save storage and transfer faster

---

## ❓ WHY ARCHIVE & COMPRESSION IMPORTANT

- Save disk space  
- Easy file transfer  
- Backup and restore  
- Used in DevOps deployments  

---

## 🔍 COMMON FILE FORMATS

- `.tar` → archive only  
- `.gz` → compressed file  
- `.tar.gz` → archive + compression  
- `.zip` → archive + compression  

---

## 📦 TAR COMMAND (ARCHIVE)

Create archive:
`tar -cvf file.tar files/`

Extract archive:
`tar -xvf file.tar`

View archive:
`tar -tvf file.tar`

Options:

- c → create  
- x → extract  
- v → verbose  
- f → file  

---

## 🗜️ GZIP (COMPRESSION)

Compress file:
`gzip file.txt`

👉 Output: `file.txt.gz`

Decompress:
`gunzip file.txt.gz`

---

## 🔗 TAR + GZIP

Create compressed archive:
`tar -czvf file.tar.gz files/`

Extract:
`tar -xzvf file.tar.gz`

---

## 🗜️ BZIP2 (BETTER COMPRESSION)

Compress:
`bzip2 file.txt`

Decompress:
`bunzip2 file.txt.bz2`

Tar with bzip:
`tar -cjvf file.tar.bz2 files/`

Extract:
`tar -xjvf file.tar.bz2`

---

## 📁 ZIP (COMMON FORMAT)

Create zip:
`zip file.zip file1 file2`

Extract:
`unzip file.zip`

---

## ⚡ DIFFERENCE

| Tool | Purpose |
|------|--------|
| tar | Archive only |
| gzip | Fast compression |
| bzip2 | Better compression |
| zip | Cross-platform |

---

## 🔄 REAL SCENARIO

👉 Backup project folder:

`tar -czvf backup.tar.gz project/`

👉 Send file to server → extract:

`tar -xzvf backup.tar.gz`

---

## ⚠️ COMMON MISTAKES

- Confusing tar and gzip  
- Forgetting options (c, x, f)  
- Wrong extraction command  

---

## 🔒 SECURITY TIP

- Verify files before extracting  
- Avoid unknown archives  

---

## 🏆 GOLDEN RULES

- Use tar + gzip for backups  
- Use zip for sharing  
- Practice commands  

---

## 🎤 INTERVIEW QUESTIONS

- Difference between tar and gzip?  
- What is .tar.gz file?  
- Which compression is best?  

---

## 🧪 PRACTICE LAB

Create files:
`touch a.txt b.txt`

Archive:
`tar -cvf test.tar a.txt b.txt`

Compress:
`gzip test.tar`

Extract:
`tar -xzvf test.tar.gz`

---

## 💡 QUICK COMMANDS

`tar -cvf file.tar`  
`tar -xvf file.tar`  
`tar -czvf file.tar.gz`  
`tar -xzvf file.tar.gz`  
`gzip file`  
`gunzip file.gz`  
`zip file.zip`  
`unzip file.zip`  
