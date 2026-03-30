## ⚙️ What is Operating System?

### ✅ What
An Operating System (OS) is system software that manages computer hardware and software resources and acts as an interface between user and hardware.

### ❓ Why OS is needed?
- To manage hardware (CPU, Memory, Disk)
- To run applications (Chrome, VS Code, etc.)
- To provide user interface (CLI/GUI)
- To handle processes and files

### ⚙️ How OS works?
1. User gives command (CLI/GUI)
2. OS receives the request
3. Kernel processes the request
4. Hardware executes it
5. Output is shown to user

---

## 🧠 Linux Architecture (Detailed)

Linux architecture is divided into **4 main layers**:

### 1️⃣ Hardware

#### 📌 Definition:
Physical components of a computer system.

#### 💡 Examples:
- CPU (Processor)
- RAM (Memory)
- Hard Disk (Storage)
- Network Devices

#### ❓ Why important?
Without hardware, OS cannot run.

---

### 2️⃣ Kernel (Heart of Linux)

#### 📌 Definition:
Kernel is the core part of the Linux OS that directly interacts with hardware.

#### ⚙️ Responsibilities:
- Process Management  
- Memory Management  
- Device Management  
- File System Management  

#### ❓ Why important?
- Kernel acts as a bridge between software and hardware  
- Without kernel, system cannot function  

#### ⚙️ How it works?
- Takes request from shell/application  
- Converts it into low-level instructions  
- Sends it to hardware  

---

### 3️⃣ Shell

#### 📌 Definition:
Shell is a command-line interface that allows users to interact with the kernel.

#### 💡 Examples:
- bash  
- sh  
- zsh  

#### ❓ Why important?
- Users cannot directly talk to kernel  
- Shell makes communication easy  

#### ⚙️ How it works?
- User types command  
- Shell interprets it  
- Sends to kernel  

---

### 4️⃣ Applications / User Space

#### 📌 Definition:
All user-level programs that run on Linux.

#### 💡 Examples:
- Browser  
- Text Editor  
- Games  
- DevOps tools  

#### ❓ Why important?
- Users interact with system through applications  

---

## 🔄 Flow of Linux Architecture

```text
User → Application → Shell → Kernel → Hardware
