<!-- PROJECT TITLE -->
<h1 align="center">🔐 AWS IAM Project – Secure Multi-User Access Management</h1>
<img width="300" height="500" alt="img3-1" src="https://github.com/user-attachments/assets/05a4fab8-1fd2-4ca1-9e92-172d7466898f" /> 
<img width="300" height="400" alt="img3-1" src="https://github.com/user-attachments/assets/b3b03456-520d-45cf-8a64-91f21fb29605"/>
     <img width="302" height="300" alt="img2" src="https://github.com/user-attachments/assets/352b888f-eb40-43dd-ad71-5e31120b6935"/>





<p align="center">
  <strong>Identity & Access Management | Cloud Security | AWS Best Practices</strong><br>
  <img src="https://img.shields.io/badge/AWS-IAM-orange?logo=amazon" />
  <img src="https://img.shields.io/badge/Cloud-Security-blue" />
  <img src="https://img.shields.io/badge/Status-Completed-green" />
</p>

---

## 📌 Project Overview
This project demonstrates how to design a **secure AWS IAM Architecture** using  
Users, Groups, Roles, Custom Policies, MFA, and Least-Privilege Access.

A real-world scenario used by Cloud Engineers, DevOps, and Security Teams.

---

## 🧱 Architecture Summary

### 👤 **Users**
- `dev1`, `dev2`  
- `admin1`  
- `auditor1`

### 👥 **Groups**
- **DevGroup** → ReadOnlyAccess  
- **AdminGroup** → AdministratorAccess  
- **AuditGroup** → SecurityAudit  

### 🎭 **IAM Role**
- `EC2-S3-Access-Role`  
⮞ Allows EC2 to access S3 without Access Keys.

### 📜 **Policies**
- AWS Managed Policies  
- Custom JSON Policies  
- MFA Enforcement Policy  
- S3 Developer ReadOnly Policy  

## 🛠 Implementation Steps

### 🔹 **Step 1 — Create IAM Users**
- Enable console password  
- Force password reset  
- Assign to correct groups  

---

### 🔹 **Step 2 — Create IAM Groups**
| Group Name | Permission |
|-----------|------------|
| DevGroup | ReadOnlyAccess |
| AdminGroup | AdministratorAccess |
| AuditGroup | SecurityAudit |

---

### 🔹 **Step 3 — Create Custom Policies**

#### ✔ Developer S3 ReadOnly Policy (`policies/dev-readonly-policy.json`)
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:Get*",
        "s3:List*"
      ],
      "Resource": "*"
    }
  ]
}
```

#### ✔ MFA Enforcement Policy (`policies/mfa-required.json`)
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Deny",
      "Action": "*",
      "Resource": "*",
      "Condition": {
        "BoolIfExists": { "aws:MultiFactorAuthPresent": "false" }
      }
    }
  ]
}
```

---

### 🔹 **Step 4 — Create IAM Role for EC2**
- Role Name: `EC2-S3-Access-Role`  
- Trusted Entity: EC2  
- Permission: AmazonS3FullAccess  
- Attach role to EC2 instance  

---

### 🔹 **Step 5 — Set Account Alias**
Example:  
```
company-secure-login
```
Login URL becomes:  
```
https://company-secure-login.signin.aws.amazon.com/console
```

---

### 🔹 **Step 6 — Apply Password & Security Policy**
- Minimum length: 12  
- Require uppercase, numbers, symbols  
- Password expiration: 90 days  

---

### 🔹 **Step 7 — Access Key Rotation**
Performed for `dev1` and `dev2`.

---

## 📂 Folder Structure
```
aws-iam-project/
│
├── README.md
├── architecture-diagram.png
├── policies/
│   ├── dev-readonly-policy.json
│   ├── mfa-required.json
│   └── s3-fullaccess-policy.json
└── screenshots/
    ├── create-user.png
    ├── create-group.png
    ├── attach-policy.png
    ├── role-creation.png
    ├── mfa-setup.png
    └── login-alias.png
`
## 🎯 What I Learned
✔ IAM Best Practices  
✔ Role-Based Access Control  
✔ JSON Policy Creation  
✔ MFA + Security Hardening  
✔ Account Security Design  
✔ EC2 Role Authentication  
✔ Cloud Architecture Documentation  

---

## 🛡 Skills Used
- AWS IAM  
- Cloud Security  
- Identity & Access Management  
- JSON Policy Writing  
- DevOps Fundamentals  
- Access Control Architecture  

---

## 🏁 Project Status
**✔ Completed Successfully**  
This project strengthens core AWS security & IAM skills required for Cloud Engineer, DevOps Engineer, and Network Engineer roles.

---

<h3 align="center">⭐ If you like this project, give it a star on GitHub! ⭐</h3>

