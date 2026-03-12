# 🔐 AWS CloudTrail Threat Detection & Alerting System

A serverless, event-driven cloud security monitoring pipeline that automatically analyzes AWS CloudTrail logs, detects suspicious activity in near real-time, and delivers automated alerts - built to reflect real-world SOC practices.

> 📺 **[Watch Demo Video](https://github.com/user-attachments/assets/f8a922dd-c65a-442c-8863-d9cbd8eb9bf4)** &nbsp;|&nbsp; 🛠️ **AWS, Python, Lambda, DynamoDB, SNS, API Gateway**

---

## 📌 Overview

Cloud environments generate massive volumes of security logs. Manual monitoring is slow, error-prone, and leaves organizations exposed. This project automates the full detection-to-alert lifecycle using a fully serverless AWS architecture - detecting threats in **under 10 seconds** with **sub-millisecond query latency**.

---

## ⚙️ Architecture

```
https://github.com/user-attachments/assets/7fd2e478-31bf-4996-8602-7d8d11ea8e64
```

| AWS Service        | Role                                               |
|--------------------|----------------------------------------------------|
| AWS CloudTrail     | Generates audit logs for all AWS account activity  |
| Amazon S3          | Secure storage for CloudTrail `.json.gz` log files |
| AWS Lambda         | Serverless Python-based detection engine           |
| Amazon DynamoDB    | Centralized NoSQL alert storage                    |
| Amazon SNS         | Real-time email alert notifications                |
| Amazon API Gateway | REST API (`/alerts`) for analyst access            |

---

## 🚨 Threat Detection Rules

The Lambda detection engine identifies the following high-risk events:

- **MFA Bypass** - Console logins without multi-factor authentication
- **Unauthorized API Calls** - `AccessDenied` events across AWS services
- **CloudTrail Tampering** - Attempts to disable or modify audit logging

Each alert is assigned a severity level and stored in DynamoDB with full event metadata.

---

## 🔒 Security Practices

- **Least-privilege IAM roles** - each service only has the permissions it needs
- **Encryption at rest** - enabled on both S3 and DynamoDB
- **HTTPS enforced** - via API Gateway for all REST endpoints
- **Full auditability** - CloudTrail logs all actions taken within the system itself

---

## 📊 Key Metrics

| Metric                    | Value                    |
|---------------------------|--------------------------|
| Detection latency         | < 10 seconds             |
| Security events processed | 100+                     |
| DynamoDB query latency    | Sub-millisecond          |
| Architecture cost model   | Serverless (pay-per-use) |

---

## 🔮 Future Enhancements

- [ ] Web-based dashboard for alert visualization
- [ ] Integration with threat intelligence feeds (e.g. MISP, VirusTotal)
- [ ] Expanded detection rules (privilege escalation, data exfiltration)
- [ ] SIEM integration (Elastic, Splunk)
