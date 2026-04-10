# 📦 AWS S3 (Simple Storage Service)

> 📚 Complete S3 Guide (Beginner → Intermediate → Practical)  
> ⚡ Highly scalable object storage service in AWS

---

# 🔹 What is S3?

Amazon S3 is an object storage service used to store and retrieve any amount of data from anywhere over the internet.

👉 It stores data as:
- Objects (files)
- Inside Buckets (containers)

---

# 🔹 Why S3 is Needed?

- Store unlimited data  
- Highly durable and available  
- Accessible from anywhere  
- Used for backups, static websites, logs, media  

---

# 🔹 Basic Terminology

## 🔹 Bucket
A bucket is a container used to store objects.

## 🔹 Object
An object is a file along with its metadata.

## 🔹 Key
A key is the unique name of an object inside a bucket.

---

# 🔹 How S3 Works

1. User uploads file to bucket  
2. File is stored as an object  
3. Each object has a unique key  
4. Data can be retrieved using the key  

---

# 🔥 S3 Storage Classes

## 🔹 Standard
- High availability  
- Frequently accessed data  

---

## 🔹 Standard-IA (Infrequent Access)
- Lower cost  
- For less frequently accessed data  

---

## 🔹 One Zone-IA
- Stored in single availability zone  
- Cheaper but less resilient  

---

## 🔹 Glacier
- Archival storage  
- Slow retrieval  

---

## 🔹 Glacier Deep Archive
- Lowest cost  
- Long-term backup  

---

# 🔐 S3 Security

## 🔹 Bucket Policy
Controls access at bucket level.

## 🔹 IAM Policy
Controls user access.

## 🔹 ACL (Access Control List)
Legacy method to control access.

## 🔹 Encryption
- Server-side encryption (SSE)  
- Client-side encryption  

---

# 🔑 Access Control

- Private (default)  
- Public (manual enable)  
- Pre-signed URLs (temporary access)  

---

# 🔄 Versioning

- Keeps multiple versions of objects  
- Helps in recovery from deletion or overwrite  

---

# 🔁 Lifecycle Management

- Automatically move objects between storage classes  
- Delete old data  

---

# 🌐 Static Website Hosting

S3 can host static websites:
- HTML, CSS, JS files  
- No backend required  

---

# 🔄 Data Consistency

- Strong read-after-write consistency  
- Immediate access after upload  

---

# ⚙️ S3 Features

- Unlimited storage  
- High durability (99.999999999%)  
- Event notifications  
- Cross-region replication  

---

# 🔍 Real Use Cases

- Backup and restore  
- Static website hosting  
- Log storage  
- Media storage (images/videos)  

---

# ⚠️ Common Mistakes

- Making bucket public accidentally  
- No versioning enabled  
- No lifecycle rules  
- Incorrect permissions  

---

# 🔒 Best Practices

- Enable versioning  
- Use least privilege  
- Enable encryption  
- Block public access unless needed  
- Use lifecycle policies  

---

# 🏆 Interview Questions

- What is S3?  
- What is a bucket?  
- What is versioning?  
- What are storage classes?  
- Difference between S3 and EBS?  

---

# 🧪 Practical Steps

## Create Bucket

1. Go to S3 console  
2. Click Create Bucket  
3. Enter bucket name  
4. Choose region  
5. Configure settings  
6. Create  

---

## Upload File

1. Open bucket  
2. Click Upload  
3. Select file  
4. Upload  

---

# 💡 Quick Revision

S3 = Object storage  
Bucket = Container  
Object = File  
Key = Unique name  
Versioning = Backup  
Lifecycle = Automation  

---

# 🎯 Final Concept

S3 is a scalable, secure, and durable object storage service used to store and manage data in AWS.
