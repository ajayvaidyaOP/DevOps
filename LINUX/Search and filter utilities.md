# 🔍 LINUX SEARCH & FILTER UTILITIES

![Linux](https://img.shields.io/badge/Linux-Search_&_Filter-blue)
![Level](https://img.shields.io/badge/Level-Beginner_to_Advanced-green)
![DevOps](https://img.shields.io/badge/DevOps-Core-orange)

> 📚 Complete Guide to Search & Filter Commands in Linux  
> ⚡ Used to find, filter, and process data efficiently

---

## 📌 WHAT ARE SEARCH & FILTER UTILITIES

Search & filter utilities are commands used to:
- Find files  
- Search text  
- Filter output  
- Process data  

---

## ❓ WHY IMPORTANT

- Handle large data  
- Used in automation  
- Important for logs & debugging  
- Core DevOps skill  

---

## 🔍 FIND COMMAND (FILE SEARCH)

Search files:
`find /path -name file.txt`

Common usage:
- `find / -type f`  
- `find / -size +100M`  
- `find / -mtime -1`  

Delete:
`find /tmp -name "*.log" -delete`

---

## ⚡ LOCATE COMMAND (FAST SEARCH)

Search file:
`locate file.txt`

👉 Uses database (faster than find)

Update database:
`updatedb`

---

## 🔎 WHICH COMMAND

Find command location:
`which ls`

👉 Shows path of command

---

## 📍 WHEREIS COMMAND

Command info:
`whereis ls`

👉 Shows binary, source, manual  

---

## 🔍 GREP (TEXT SEARCH)

Search inside file:
`grep "text" file.txt`

Ignore case:
`grep -i "text" file.txt`

Recursive:
`grep -r "text" /dir`

---

## 🧰 EGREP / FGREP

Extended grep:
`egrep "pattern" file`

Fixed string:
`fgrep "text" file`

---

## 🔧 AWK (ADVANCED FILTER)

Print column:
`awk '{print $1}' file.txt`

Filter:
`awk '$1=="error"' file.txt`

---

## ✂️ SED (STREAM EDITOR)

Replace text:
`sed 's/old/new/g' file.txt`

Delete line:
`sed '1d' file.txt`

---

## 🔢 SORT

Sort file:
`sort file.txt`

Reverse:
`sort -r file.txt`

---

## 🔄 UNIQUE

Remove duplicates:
`uniq file.txt`

---

## 🔢 WC (WORD COUNT)

Count lines:
`wc -l file.txt`

Count words:
`wc -w file.txt`

---

## 🔍 HEAD

Show first lines:
`head file.txt`

---

## 🔍 TAIL

Show last lines:
`tail file.txt`

Live logs:
`tail -f file.txt`

---

## 🔎 CUT

Extract columns:
`cut -d " " -f1 file.txt`

---

## 🔗 TR (TRANSLATE)

Convert case:
`tr 'a-z' 'A-Z'`

---

## 🔄 PIPE (|)

Combine commands:

Example:
`ps -ef | grep nginx`

---

## 🔄 REAL SCENARIO

👉 Find error logs:

`grep "error" app.log`

👉 Monitor logs:

`tail -f app.log | grep error`

👉 Find large files:

`find / -size +500M`

---

## ⚠️ COMMON MISTAKES

- Using find instead of locate  
- Not using pipes  
- Wrong grep pattern  

---

## 🔒 SECURITY TIP

- Avoid searching full system unnecessarily  
- Check before delete  

---

## 🏆 GOLDEN RULES

- Use locate for speed  
- Use find for accuracy  
- Combine with pipes  

---

## 🎤 INTERVIEW QUESTIONS

- Difference between find and locate?  
- What is grep?  
- What is awk vs sed?  
- What is pipe?  

---

## 🧪 PRACTICE LAB

Search file:
`find . -name test.txt`

Search text:
`grep "hello" file.txt`

Sort:
`sort file.txt`

Count:
`wc -l file.txt`

---

## 💡 QUICK COMMANDS

`find`  
`locate`  
`grep`  
`awk`  
`sed`  
`sort`  
`uniq`  
`wc`  
`head`  
`tail`  
`cut`  
`tr`  
