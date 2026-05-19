# 🚀 Hosting a Static Website on NGINX using AWS EC2 (Ubuntu)

> A beginner-friendly DevOps project demonstrating how to deploy a static website using **NGINX** on an **AWS EC2 Ubuntu instance**.

---

# 📚 Table of Contents

* [📖 Project Overview](#-project-overview)
* [🛠️ Prerequisites](#️-prerequisites)
* [🧭 Step 1 — Launch EC2 Instance](#-step-1--launch-ec2-instance)
* [⚙️ Step 2 — Install NGINX](#️-step-2--install-nginx)
* [📄 Step 3 — Create Custom Web Page](#-step-3--create-custom-web-page)
* [🌐 Step 4 — Access the Website](#-step-4--access-the-website)
* [🏗️ Architecture Diagram](#️-architecture-diagram)
* [🔒 Best Practices](#-best-practices)
* [🚀 Future Enhancements](#-future-enhancements)
* [🎯 Skills Demonstrated](#-skills-demonstrated)
* [🎉 Conclusion](#-conclusion)

---

# 📖 Project Overview

This project demonstrates how to:

✅ Launch an Ubuntu EC2 instance on AWS
✅ Install and configure NGINX Web Server
✅ Create and host a custom static webpage
✅ Access the website publicly using EC2 Public IP

This practical helps build a strong foundation in:

* Linux Administration
* AWS EC2
* Web Server Configuration
* Networking Basics
* DevOps Fundamentals

---

# 🛠️ Prerequisites

Before starting, ensure you have:

* An AWS Account
* Basic Linux knowledge
* EC2 Instance Connect or SSH Client
* Internet Connectivity

---

# 🧭 Step 1 — Launch EC2 Instance

Navigate to:

```text
AWS Console → EC2 → Launch Instance
```

---

## 📋 EC2 Configuration

| Setting          | Value                     |
| ---------------- | ------------------------- |
| Instance Name    | nginx-host                |
| Operating System | Ubuntu                    |
| Instance Type    | t3.micro                  |
| Key Pair         | Create or Select Existing |
| Security Group   | Allow HTTP & SSH          |

---

## 🔓 Security Group Rules

Allow the following inbound ports:

| Service | Port |
| ------- | ---- |
| SSH     | 22   |
| HTTP    | 80   |

---

# ⚙️ Step 2 — Install NGINX

Connect to your EC2 instance and run:

```bash
sudo apt update -y
sudo apt install nginx -y
```

---

## 🔍 Verify NGINX Status

```bash
sudo systemctl status nginx
```

---

# 📄 Step 3 — Create Custom Web Page

Create a custom HTML page:

```bash
echo "This is NGINX Custom Page" > index.html
```

Verify the file:

```bash
ls
```

---

## 📂 Copy Web Page to NGINX Directory

```bash
sudo cp index.html /var/www/html/
```

---

## 🔄 Restart NGINX Service

```bash
sudo systemctl restart nginx
```

---

# 🌐 Step 4 — Access the Website

Copy the **Public IPv4 Address** from EC2 Dashboard.

Example:

```text
54.234.114.254
```

Open in browser:

```text
http://<your-public-ip>
```

---

# ✅ Expected Output

```text
This is NGINX Custom Page
```

---

# 🏗️ Architecture Diagram

```text
+----------------------+
|      End User        |
|    Web Browser       |
+----------+-----------+
           |
           | HTTP Request (Port 80)
           ▼
+----------------------+
| AWS Internet Gateway |
+----------+-----------+
           |
           ▼
+----------------------------------+
| EC2 Instance (Ubuntu)            |
|                                  |
| +------------------------------+ |
| |       NGINX Web Server       | |
| |          Port 80             | |
| +--------------+---------------+ |
|                |                 |
|                ▼                 |
|      /var/www/html              |
|         index.html              |
+----------------------------------+
           |
           ▼
      HTTP Response
```

---

# 🧭 Architecture Explanation

1. User accesses EC2 Public IP using browser
2. Request reaches AWS Internet Gateway
3. Traffic forwarded to EC2 instance
4. NGINX listens on Port 80
5. Static content served from `/var/www/html`
6. Response returned to browser

---

# 🔒 Best Practices

For production-level deployment:

* Use Elastic IP for static public IP
* Restrict SSH access to your IP only
* Enable HTTPS using Certbot
* Configure custom domain using Route 53
* Use Application Load Balancer (ALB)
* Enable CloudWatch monitoring
* Configure Auto Scaling

---

# 🚀 Future Enhancements

You can improve this project further using:

* Terraform (Infrastructure as Code)
* GitHub Actions (CI/CD)
* Docker Containerization
* Kubernetes Deployment
* Reverse Proxy Configuration
* Monitoring & Alerting
* SSL/TLS Setup

---

# 🎯 Skills Demonstrated

* AWS EC2
* Ubuntu Linux
* NGINX Installation
* SSH Access
* Linux Commands
* Networking Basics
* Static Website Hosting
* DevOps Fundamentals

---

# 🎉 Conclusion

In this project, you successfully:

✅ Launched an AWS EC2 Ubuntu instance
✅ Installed and configured NGINX
✅ Hosted a static website
✅ Accessed the application publicly using EC2 Public IP

This project provides a strong foundation for advanced DevOps and Cloud technologies including Docker, Kubernetes, Terraform, CI/CD pipelines, and cloud-native deployments.

---

# 👨‍💻 Author

## Yogesh Ade

### Aspiring DevOps Engineer | Linux | AWS | Cloud Computing | Automation

---
