# 🔐 Secure File Transfer to AWS EC2 Using `scp -i`

> ### 🚀 A Complete Hands-On Practical Guide for Secure File Transfer Between Local Machine and AWS EC2

---

# 📚 Table of Contents

* [📖 Introduction](#-introduction)
* [🎯 Objective](#-objective)
* [🛠️ Prerequisites](#️-prerequisites)
* [☁️ Step 1 — Launch an AWS EC2 Instance](#️-step-1--launch-an-aws-ec2-instance)
* [🔑 Step 2 — Generate SSH Key Pair](#-step-2--generate-ssh-key-pair)
* [📤 Step 3 — Transfer Files Using `scp -i`](#-step-3--transfer-files-using-scp--i)
* [🔐 Step 4 — Connect to EC2 Using SSH](#-step-4--connect-to-ec2-using-ssh)
* [✅ Step 5 — Verify File Transfer](#-step-5--verify-file-transfer)
* [📊 Architecture Workflow](#-architecture-workflow)
* [🔒 Security Best Practices](#-security-best-practices)
* [🧠 Key Learning Outcomes](#-key-learning-outcomes)
* [📝 Conclusion](#-conclusion)
* [📚 References](#-references)

---

# 📖 Introduction

`scp` (**Secure Copy Protocol**) is a Linux command-line utility used to securely transfer files between systems over an encrypted SSH connection.

In AWS cloud environments, `scp -i` is commonly used to upload files from a local machine to an EC2 instance using a `.pem` authentication key.

This practical demonstrates:

✅ SSH Key Generation
✅ Secure File Transfer
✅ AWS EC2 Authentication
✅ Remote Linux File Verification
✅ Secure Remote Access

---

# 🎯 Objective

The main objective of this practical is to:

* Generate SSH key pairs
* Transfer files securely to AWS EC2
* Understand SCP authentication
* Learn secure Linux remote communication
* Practice real-world DevOps and cloud administration tasks

---

# 🛠️ Prerequisites

Before starting this practical, ensure the following requirements are completed.

| Requirement       | Description               |
| ----------------- | ------------------------- |
| ☁️ AWS Account    | Active AWS account        |
| 🖥️ EC2 Instance  | Ubuntu Linux EC2 instance |
| 🔑 Key Pair       | `.pem` authentication key |
| 🌐 Public IP      | Public IP address of EC2  |
| 🔓 Security Group | SSH Port 22 allowed       |
| 💻 Local Machine  | Windows/Linux/Mac         |
| ⚙️ Tools          | `ssh` and `scp` installed |

---

# ☁️ Step 1 — Launch an AWS EC2 Instance

## 🔹 Procedure

1. Login to the AWS Management Console
2. Open the **EC2 Dashboard**
3. Click **Launch Instance**
4. Select **Ubuntu AMI**
5. Choose instance type (`t2.micro` or `t3.micro`)
6. Create or select an existing key pair
7. Configure Security Group:

   * Allow SSH (Port 22)
8. Launch the instance
9. Copy the Public IPv4 address

---

## 📷 EC2 Instance Overview

```text id="av6vzt"
Instance Name : ssh-keygen
Instance Type : t3.micro
Operating OS  : Ubuntu
Status        : Running
```

---

# 🔑 Step 2 — Generate SSH Key Pair

Move to the Downloads directory:

```bash id="1rxg2w"
cd Downloads
```

Generate SSH keys:

```bash id="9c0r18"
ssh-keygen
```

---

## 🔹 Example Output

```text id="0osqsv"
Generating public/private ed25519 key pair.
Enter file in which to save the key: john
```

---

## 🔹 Generated Files

| File       | Purpose     |
| ---------- | ----------- |
| `john`     | Private Key |
| `john.pub` | Public Key  |

---

## 📷 SSH Key Generation

```bash id="g14k1q"
ssh-keygen
```

This command generates secure authentication keys used for encrypted SSH communication.

---

# 📤 Step 3 — Transfer Files Using `scp -i`

## 🔹 SCP Command Syntax

```bash id="8sl9fz"
scp -i <pem-file> <source-file> <username>@<public-ip>:<destination-path>
```

---

## 🔹 Real Practical Command

```bash id="cz9m6s"
scp -i YOGESH.pem john.pub ubuntu@184.72.111.80:/home/ubuntu
```

---

# 📘 Command Breakdown

| Component       | Description                    |
| --------------- | ------------------------------ |
| `scp`           | Secure Copy Command            |
| `-i`            | Identity file option           |
| `YOGESH.pem`    | AWS private authentication key |
| `john.pub`      | File being transferred         |
| `ubuntu`        | Default Ubuntu username        |
| `184.72.111.80` | EC2 public IP address          |
| `/home/ubuntu`  | Destination directory          |

---

## 🔹 First-Time Authentication Prompt

During the first connection:

```text id="0c7c9z"
The authenticity of host can't be established.
Are you sure you want to continue connecting?
```

Type:

```bash id="p4t0fk"
yes
```

The host will be added to the known hosts list, and the transfer will begin securely.

---

## 📷 SCP File Transfer Success

```text id="8s50kq"
john.pub                                   100%
```

This confirms that the file has been successfully uploaded to the EC2 server.

---

# 🔐 Step 4 — Connect to EC2 Using SSH

Connect to the EC2 instance using:

```bash id="ldnd8n"
ssh -i YOGESH.pem ubuntu@184.72.111.80
```

---

## 📷 Successful SSH Login

```text id="h6wm10"
Welcome to Ubuntu 26.04 LTS
```

This indicates successful authentication and remote server access.

---

# ✅ Step 5 — Verify File Transfer

Check whether the file exists on the EC2 server.

```bash id="j4m6sk"
ls
```

---

## 🔹 Expected Output

```text id="s09mxr"
john.pub
```

---

## 🔹 Detailed Verification

```bash id="mnx4va"
ls -l /home/ubuntu
```

This command displays file permissions, ownership, and timestamps.

---

# 📊 Architecture Workflow

```text id="g83uxv"
+------------------------+
|   Local Windows PC     |
|                        |
|   john.pub File        |
+------------+-----------+
             |
             |  SCP Secure Transfer
             |  Using SSH + .pem Key
             v
+-------------------------+
|   AWS EC2 Ubuntu        |
|                         |
|   /home/ubuntu          |
+-------------------------+
```

---

# 🔒 Security Best Practices

## 🔹 Protect the `.pem` File

Never share your private key publicly.

---

## 🔹 Restrict File Permissions

```bash id="jryp6n"
chmod 400 YOGESH.pem
```

---

## 🔹 Limit SSH Access

Inside the AWS Security Group:

* Allow only trusted IP addresses
* Avoid opening Port 22 publicly to everyone

---

## 🔹 Use Public/Private Key Authentication

Key-based authentication is safer than password authentication.

---

# 🧠 Key Learning Outcomes

After completing this practical, you will understand:

✅ SSH Authentication
✅ SCP File Transfer
✅ AWS EC2 Connectivity
✅ Linux Remote Administration
✅ Secure Cloud Communication
✅ Key-Based Authentication
✅ Basic DevOps Remote Operations

---

# 📝 Conclusion

Using `scp -i`, files can be securely transferred between a local machine and an AWS EC2 instance through encrypted SSH communication.

This practical demonstrates real-world Linux and AWS administration concepts commonly used in:

* ☁️ Cloud Computing
* ⚙️ DevOps Engineering
* 🐧 Linux Administration
* 🔐 Secure Remote Access
* 🚀 Infrastructure Management

The `scp` command is one of the most essential tools for secure file management in cloud environments.

---
