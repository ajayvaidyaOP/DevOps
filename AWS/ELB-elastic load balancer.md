# ⚖️ AWS ELB (Elastic Load Balancer)

> 📚 Complete Load Balancer Guide (Beginner → Intermediate → Practical)  
> ⚡ Distributes incoming traffic across multiple targets

---

# 🔹 What is ELB?

Elastic Load Balancer (ELB) automatically distributes incoming application traffic across multiple targets such as EC2 instances.

👉 Targets can be:
- EC2 instances  
- Containers  
- IP addresses  

---

# 🔹 Why ELB is Needed?

- Avoid single point of failure  
- Improve availability  
- Handle high traffic  
- Ensure fault tolerance  

---

# 🔹 How ELB Works

1. Client sends request  
2. Request hits Load Balancer  
3. Load Balancer distributes traffic  
4. Targets respond  

---

# 🔥 Types of Load Balancers

---

## 🔹 Application Load Balancer (ALB)

- Works at Layer 7 (HTTP/HTTPS)  
- Content-based routing  
- Supports microservices  

👉 Example:
Route traffic based on URL (/api, /login)

---

## 🔹 Network Load Balancer (NLB)

- Works at Layer 4 (TCP/UDP)  
- High performance  
- Low latency  

👉 Used for:
- Real-time applications  
- High throughput systems  

---

## 🔹 Classic Load Balancer (CLB)

- Legacy load balancer  
- Not recommended for new applications  

---

# 🔥 Key Components

## 🔹 Listener

- Listens for incoming traffic  
- Example: HTTP (80), HTTPS (443)  

---

## 🔹 Target Group

- Group of targets (EC2, IP, etc.)  
- Routes traffic to registered targets  

---

## 🔹 Health Check

- Checks if targets are healthy  
- Sends traffic only to healthy instances  

---

# 🔹 Routing

- Round-robin (default)  
- Based on rules (ALB)  

---

# 🔐 Security

## 🔹 Security Groups

- Control inbound/outbound traffic  

## 🔹 SSL/TLS

- Supports HTTPS  
- SSL termination at load balancer  

---

# 🔄 Integration

- Works with Auto Scaling  
- Works with EC2, ECS, EKS  
- Integrated with Route 53  

---

# 🔄 High Availability

- Deployed across multiple Availability Zones  
- Automatically distributes traffic  

---

# 🔍 Real Use Cases

- Web applications  
- Microservices architecture  
- Load distribution  
- Fault tolerance  

---

# ⚠️ Common Mistakes

- Not configuring health checks  
- Wrong target group setup  
- Using wrong type of load balancer  
- Not enabling HTTPS  

---

# 🔒 Best Practices

- Use ALB for web apps  
- Use NLB for high performance  
- Enable health checks  
- Use HTTPS  
- Combine with Auto Scaling  

---

# 🏆 Interview Questions

- What is ELB?  
- Difference between ALB and NLB?  
- What is a target group?  
- What is health check?  
- How does load balancing work?  

---

# 🧪 Practical Steps

## Create Load Balancer

1. Go to EC2 Dashboard  
2. Click Load Balancers  
3. Create Load Balancer  
4. Choose type (ALB/NLB)  
5. Configure listeners  
6. Create target group  
7. Register targets  

---

## Test Load Balancer

- Use DNS name of load balancer  
- Access from browser  

---

# 💡 Quick Revision

ELB = Traffic distributor  
ALB = Layer 7 (HTTP)  
NLB = Layer 4 (TCP)  
Target Group = Backend servers  
Health Check = Instance status  

---

# 🎯 Final Concept

ELB ensures high availability and scalability by distributing traffic across multiple resources and routing requests only to healthy targets.
