# Aws-security-projects-01
# 🔐 AWS IAM Project – Secure Multi-User Access Management

<p align="center">
  <strong>AWS IAM | Cloud Security | Least Privilege</strong><br>
  <img src="https://img.shields.io/badge/AWS-IAM-orange?logo=amazon" />
  <img src="https://img.shields.io/badge/Cloud-Security-blue" />
  <img src="https://img.shields.io/badge/Status-Completed-green" />
</p>

## 📌 Overview
This project demonstrates **secure AWS Identity & Access Management (IAM)** using
Users, Groups, Roles, Custom Policies, MFA, and Least-Privilege Access.

Designed using **real-world cloud security best practices**.

---

## 👤 IAM Setup
### Users
- `dev1`, `dev2`
- `admin1`
- `auditor1`

### Groups & Permissions
| Group | Permission |
|------|-----------|
| DevGroup | ReadOnlyAccess |
| AdminGroup | AdministratorAccess |
| AuditGroup | SecurityAudit |

### IAM Role
- **EC2-S3-Access-Role**
- Enables EC2 to access S3 **without access keys**

---

## 📜 Policies
- AWS Managed Policies
- Custom JSON Policies
- MFA Enforcement Policy
- Developer S3 ReadOnly Policy

---

## 🛠 Key Implementation
- IAM users with forced password reset
- Group-based access control
- Custom least-privilege policies
- MFA enforcement
- EC2 IAM Role authentication
- Password & security hardening
- Access key rotation

---

## 📂 Project Structure
aws-iam-project/
├── README.md
├── policies/
├── screenshots/
└── architecture-diagram.png

---

## 🎯 Skills Gained
- AWS IAM & Cloud Security
- Role-Based Access Control (RBAC)
- JSON Policy Writing
- MFA & Account Hardening
- Secure Cloud Architecture

---

## 🏁 Status
✔ **Completed Successfully**

⭐ *If you find this project useful, give it a star on GitHub!*
