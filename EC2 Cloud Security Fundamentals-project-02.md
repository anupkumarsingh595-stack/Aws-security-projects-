# 🔐 Secure EC2 Cloud Security Fundamentals

A comprehensive, hands-on AWS project demonstrating how to securely deploy, configure, harden, monitor, and manage an Amazon EC2 instance using AWS best practices and Infrastructure as Code.

---

## 📌 Overview
This project provides a practical introduction to cloud security by showcasing how to secure an Amazon EC2 instance from both **network** and **operating system** perspectives.

It is designed for **beginners and early-career cloud practitioners** and follows industry-aligned security standards such as:
- Least-privilege access
- Secure authentication
- OS hardening
- Continuous monitoring
- Infrastructure as Code (Terraform)

---

## 🎯 Learning Objectives
By completing this project, you will be able to:

- Securely launch and manage an EC2 instance
- Configure security groups using least-privilege principles
- Implement SSH key-based authentication
- Harden Linux OS security
- Monitor EC2 performance using Amazon CloudWatch
- Provision infrastructure using Terraform

---

## 🧩 Prerequisites
- Basic understanding of cloud computing
- An active AWS account (Free Tier eligible)
- Basic knowledge of Linux CLI
- SSH client installed (OpenSSH or PuTTY)

---

## 🛠️ Tools & Technologies
- Amazon Web Services (AWS)
- Amazon EC2
- Amazon CloudWatch
- AWS Management Console
- AWS CLI
- Terraform
- SSH (OpenSSH / PuTTY)

---

## 🏗️ Architecture Overview
**Flow:**
1. User connects via SSH using a private key.
2. Security Group restricts SSH access to a trusted IP.
3. EC2 instance runs Amazon Linux with hardened OS settings.
4. CloudWatch monitors metrics and triggers alarms.
5. Infrastructure is provisioned using Terraform.

---

## 🚀 Exercise 1: Launch an EC2 Instance

### Steps
1. Log in to AWS Management Console
2. Open EC2 Dashboard → Launch Instance
3. Select **Amazon Linux 2 AMI**
4. Choose instance type: `t2.micro`
5. Keep default instance and storage settings
6. Create a new security group:
   - Allow SSH (port 22) only from **your IP**
7. Create and download a key pair
8. Launch the instance

### ✅ Outcome
- EC2 instance running with restricted SSH access

---

## 🔑 Exercise 2: Connect to EC2 Securely

```bash
chmod 400 your-key-pair.pem
ssh -i your-key-pair.pem ec2-user@your-instance-public-dns
...bash
## 🔒 Exercise 3: OS Hardening
Update System
sudo yum update -y
sudo yum upgrade -y

Create Non-Root User
sudo adduser secureuser
sudo usermod -aG wheel secureuser

Secure SSH
sudo vi /etc/ssh/sshd_config


Set:

PermitRootLogin no
PasswordAuthentication no


Restart SSH:

sudo systemctl restart sshd

✅ Outcome

Root login disabled

Password authentication disabled

SSH key-only access enforced

🌐 Exercise 4: Security Group Hardening

Remove SSH access from 0.0.0.0/0

Allow SSH only from your public IP

✅ Outcome

Network access restricted using least privilege

📊 Exercise 5: Monitoring with CloudWatch

Create alarm for CPU utilization > 80%

Duration: 5 minutes

Enable email notification (SNS)

✅ Outcome

Proactive monitoring and alerting enabled

⚙️ Infrastructure as Code (Terraform)
Example main.tf
provider "aws" {
  region = "us-east-1"
}

resource "aws_security_group" "secure_sg" {
  ingress {
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["YOUR_IP/32"]
  }
}

resource "aws_instance" "secure_ec2" {
  ami           = "ami-xxxxxxxx"
  instance_type = "t2.micro"
  key_name      = "ec2-key"
  vpc_security_group_ids = [aws_security_group.secure_sg.id]
}

🤖 Automation Scripts (Examples)
Secure SSH Script
#!/bin/bash
sudo sed -i 's/PermitRootLogin yes/PermitRootLogin no/' /etc/ssh/sshd_config
sudo sed -i 's/PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config
sudo systemctl restart sshd

🛡️ Security Best Practices Implemented

Least-privilege security groups

SSH key-based authentication

Root login disabled

Password authentication disabled

Regular patching

Monitoring and alerting

No secrets stored in repository

🧹 Cleanup

To avoid AWS charges:

Terminate EC2 instance

Delete security groups and key pairs

Remove CloudWatch alarms
