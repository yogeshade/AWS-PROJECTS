# 🔐 AWS Practical — SSH Key Authentication on Ubuntu EC2

> **Aim:** Create a custom Linux user on an AWS Ubuntu EC2 instance and allow secure SSH login using SSH key authentication.

---

# 📚 Table of Contents

1. Overview
2. Prerequisites
3. Generate SSH Key Pair on Windows
4. Launch Ubuntu EC2 Instance
5. Connect to Ubuntu EC2
6. Copy Public Key to Server
7. Verify Public Key on Server
8. Login Using Generated SSH Key
9. Commands Quick Reference
10. Important Notes
11. Conclusion

---

# 🧭 1. Overview

This practical demonstrates how to:

* Generate SSH key pairs
* Launch an Ubuntu EC2 instance on AWS
* Connect securely using SSH
* Transfer public keys to the server
* Authenticate users using SSH keys instead of passwords

SSH key authentication is one of the most secure methods used in Linux and DevOps environments.

---

# ✅ 2. Prerequisites

| Requirement  | Details                     |
| ------------ | --------------------------- |
| AWS Account  | Active AWS account          |
| EC2 Instance | Ubuntu Linux                |
| Terminal     | CMD / PowerShell / Git Bash |
| AWS Key Pair | `.pem` file                 |
| Internet     | Public IP enabled           |

---

# 🚀 3. Generate SSH Key Pair on Windows

Move to the Downloads directory:

```bash
cd Downloads
```

Generate SSH key pair:

```bash
ssh-keygen
```

When prompted:

```text
Enter file in which to save the key: john
```

After successful execution:

```text
john       ← Private Key
john.pub   ← Public Key
```

### 🔒 Important

* `john` → Private Key (Keep Secret)
* `john.pub` → Public Key (Can be Shared)

---

# ☁️ 4. Launch Ubuntu EC2 Instance

1. Open AWS Management Console
2. Navigate to EC2 Dashboard
3. Click Launch Instance
4. Select Ubuntu Server AMI
5. Choose instance type (`t3.micro`)
6. Allow SSH access (Port 22)
7. Launch instance using AWS key pair

After launching, copy the Public IPv4 address.

Example:

```text
184.72.111.80
```

---

# 🔑 5. Connect to Ubuntu EC2

Use your AWS PEM key to connect:

```bash
ssh -i YOGESH.pem ubuntu@184.72.111.80
```

Successful login output:

```text
Welcome to Ubuntu 26.04 LTS
```

---

# 📤 6. Copy Public Key to Server

Transfer the public key file to the EC2 instance:

```bash
scp -i YOGESH.pem john.pub ubuntu@184.72.111.80:/home/ubuntu
```

If prompted:

```text
Are you sure you want to continue connecting?
```

Type:

```text
yes
```

File transfer completes successfully.

---

# 📁 7. Verify Public Key on Server

Login to the server and verify the uploaded file:

```bash
ls -l /home/ubuntu
```

Expected output:

```text
john.pub
```

This confirms the file was copied successfully.

---

# 👤 8. Login Using Generated SSH Key

Use the generated private key to connect:

```bash
ssh -i john yogesh@184.72.111.80
```

Successful login:

```text
yogesh@ip-172-31-84-6:~$
```

You are now logged in using SSH key authentication.

---

# 🛠 9. Commands Quick Reference

```bash
# Move to Downloads folder
cd Downloads

# Generate SSH key pair
ssh-keygen

# Connect to EC2 using AWS PEM key
ssh -i YOGESH.pem ubuntu@184.72.111.80

# Copy public key to server
scp -i YOGESH.pem john.pub ubuntu@184.72.111.80:/home/ubuntu

# Verify uploaded file
ls -l /home/ubuntu

# Login using generated private key
ssh -i john yogesh@184.72.111.80
```

---

# 📌 10. Important Notes

* Never share your private key publicly
* Public keys can be shared safely
* SSH authentication is more secure than password login
* Always set proper permissions on SSH keys
* Keep backup copies of important keys

---

# 🏁 11. Conclusion

In this practical, we successfully:

* Generated SSH keys using `ssh-keygen`
* Launched an Ubuntu EC2 instance
* Connected to AWS EC2 securely
* Transferred public keys using `scp`
* Verified uploaded files on Linux
* Logged in using SSH key authentication

This is a standard real-world DevOps and Linux administration practice used in cloud environments for secure server access.

---
