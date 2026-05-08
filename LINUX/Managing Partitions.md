# 💽 Linux Partition Cheatsheet

> 🚀 Complete Linux Partition Guide  
> 🔄 Learn Disk Partitioning, File Systems, Mounting, LVM, Swap & Troubleshooting

---

# 📚 Table of Contents

1. Introduction to Linux Partitioning  
2. Types of Partitions  
3. Linux File Systems  
4. Disk Management Commands  
5. Creating Partitions  
6. Formatting Partitions  
7. Mounting & Unmounting  
8. Swap Partition  
9. LVM (Logical Volume Manager)  
10. fstab Configuration  
11. Troubleshooting  
12. Best Practices  

---

# 🚀 1. Introduction to Linux Partitioning

## 🔹 What is a Partition?

A partition is a logical division of a physical disk.

It helps:

- Organize data
- Separate OS and files
- Improve management
- Increase security

---

## 🔹 Why Partition a Disk?

- Separate operating system and data
- Better backup management
- Multi-boot systems
- Improve performance
- Easier recovery

---

# 💾 2. Types of Partitions

| Partition Type | Description |
|---|---|
| Primary Partition | Main partition used for OS boot |
| Extended Partition | Special partition that contains logical partitions |
| Logical Partition | Partition created inside extended partition |
| Swap Partition | Used as virtual memory |
| Boot Partition | Contains boot loader files |

---

## 🔹 MBR vs GPT

| Feature | MBR | GPT |
|---|---|---|
| Full Form | Master Boot Record | GUID Partition Table |
| Max Partitions | 4 Primary | 128 Partitions |
| Max Disk Size | 2 TB | 9.4 ZB |
| Boot Mode | Legacy BIOS | UEFI |

---

# 🗂️ 3. Linux File Systems

| File System | Usage |
|---|---|
| ext4 | Most common Linux filesystem |
| xfs | High-performance filesystem |
| btrfs | Advanced filesystem with snapshots |
| vfat | FAT filesystem compatibility |
| ntfs | Windows filesystem support |
| swap | Virtual memory |

---

# ⚙️ 4. Disk Management Commands

## 🔹 List Disks

```bash
lsblk
```

---

## 🔹 Show Disk Details

```bash
fdisk -l
```

---

## 🔹 Check Mounted Filesystems

```bash
df -h
```

---

## 🔹 Check UUID

```bash
blkid
```

---

## 🔹 Display Filesystem Usage

```bash
du -sh /directory
```

---

# 🛠️ 5. Creating Partitions

## 🔹 Using fdisk

### Open Disk

```bash
fdisk /dev/sdb
```

---

## 🔹 Common fdisk Options

| Command | Purpose |
|---|---|
| n | Create new partition |
| p | Print partition table |
| d | Delete partition |
| w | Save changes |
| q | Quit without saving |

---

## 🔹 Example Create Partition

```bash
fdisk /dev/sdb
```

Inside fdisk:

```text
n → new partition
p → primary partition
1 → partition number
Enter → default start
Enter → default end
w → save
```

---

# 📦 6. Formatting Partitions

## 🔹 Format as ext4

```bash
mkfs.ext4 /dev/sdb1
```

---

## 🔹 Format as xfs

```bash
mkfs.xfs /dev/sdb1
```

---

## 🔹 Format as vfat

```bash
mkfs.vfat /dev/sdb1
```

---

## 🔹 Create Swap

```bash
mkswap /dev/sdb2
```

---

# 📂 7. Mounting & Unmounting

## 🔹 Create Mount Point

```bash
mkdir /data
```

---

## 🔹 Mount Partition

```bash
mount /dev/sdb1 /data
```

---

## 🔹 Verify Mount

```bash
df -h
```

---

## 🔹 Unmount Partition

```bash
umount /data
```

---

# 🔄 8. Swap Partition

## 🔹 Enable Swap

```bash
swapon /dev/sdb2
```

---

## 🔹 Disable Swap

```bash
swapoff /dev/sdb2
```

---

## 🔹 Check Swap Usage

```bash
free -h
```

---

## 🔹 Show Swap Devices

```bash
swapon --show
```

---

# ⚡ 9. LVM (Logical Volume Manager)

## 🔹 What is LVM?

LVM provides flexible disk management.

Benefits:

- Resize volumes dynamically
- Easy storage management
- Snapshots support

---

# 🔹 LVM Components

| Component | Description |
|---|---|
| PV | Physical Volume |
| VG | Volume Group |
| LV | Logical Volume |

---

## 🔹 Create Physical Volume

```bash
pvcreate /dev/sdb1
```

---

## 🔹 Create Volume Group

```bash
vgcreate myvg /dev/sdb1
```

---

## 🔹 Create Logical Volume

```bash
lvcreate -L 5G -n mylv myvg
```

---

## 🔹 Format Logical Volume

```bash
mkfs.ext4 /dev/myvg/mylv
```

---

## 🔹 Mount Logical Volume

```bash
mount /dev/myvg/mylv /data
```

---

## 🔹 Extend Logical Volume

```bash
lvextend -L +2G /dev/myvg/mylv
```

---

## 🔹 Resize Filesystem

### ext4

```bash
resize2fs /dev/myvg/mylv
```

---

### xfs

```bash
xfs_growfs /data
```

---

# ⚙️ 10. fstab Configuration

## 🔹 What is fstab?

`/etc/fstab` is used for automatic mounting during boot.

---

## 🔹 Open fstab

```bash
vi /etc/fstab
```

---

## 🔹 Example Entry

```text
UUID=xxxx-xxxx /data ext4 defaults 0 0
```

---

## 🔹 Test fstab

```bash
mount -a
```

---

# 🛠️ 11. Troubleshooting

## 🔹 Partition Not Showing

```bash
partprobe
```

---

## 🔹 Filesystem Check

```bash
fsck /dev/sdb1
```

---

## 🔹 Busy Mount Issue

```bash
lsof | grep /data
```

---

## 🔹 Check Disk Usage

```bash
df -h
```

---

## 🔹 Check Inodes

```bash
df -i
```

---

# ✅ 12. Best Practices

## 🔹 Recommended Practices

- Use GPT for modern systems
- Keep separate `/home`
- Use LVM for flexibility
- Regular backups
- Monitor disk usage
- Use UUID in fstab
- Keep swap properly configured

---

# 📚 Important Directories

| Directory | Purpose |
|---|---|
| /boot | Boot files |
| /home | User data |
| /var | Logs and variable data |
| /tmp | Temporary files |
| /etc | Configuration files |

---

# 🎯 Final Takeaway

Linux partitioning helps:

- Organize storage efficiently
- Improve system management
- Enhance performance
- Simplify backups and recovery
- Enable scalable storage with LVM

---

<p align="center">

💽 Linux Partitioning Makes Storage Management Efficient 🚀

</p>
