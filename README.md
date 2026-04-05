# aws-vpc-flowlogs-siem
Cloud Security Monitoring using AWS VPC Flow Logs and CloudWatch Logs Insights
# AWS VPC Flow Logs SIEM Project

## 📌 Overview

This project demonstrates how to build a cloud-based security monitoring solution using AWS VPC Flow Logs and CloudWatch Logs Insights.

The goal was to simulate real-world SOC (Security Operations Center) activities such as detecting SSH access attempts, identifying suspicious IP addresses, and analyzing network traffic patterns.

---

## 🛠️ Technologies Used

* AWS EC2
* AWS VPC Flow Logs
* AWS CloudWatch Logs Insights

---

## 🔍 Key Activities Performed

* Deployed EC2 instance in AWS
* Enabled VPC Flow Logs for network monitoring
* Ingested logs into CloudWatch
* Generated network traffic (ping, curl, SSH)
* Analyzed logs using Logs Insights queries

---

## 🚨 Detection Use Cases

### 1. SSH Activity Detection

Identified incoming SSH traffic on port 22.

### 2. Brute Force Detection

Detected repeated failed SSH attempts indicating possible brute-force attacks.

### 3. Top IP Identification

Analyzed top source IP addresses interacting with the instance.

### 4. Rejected Traffic Analysis

Monitored blocked connections to identify suspicious behavior.

---

## 📊 Sample Queries

### 🔹 SSH Detection

```sql
fields @timestamp, srcAddr, dstPort, action
| filter dstPort = 22
| sort @timestamp desc
```

### 🔹 Top IPs

```sql
stats count(*) as attempts by srcAddr
| sort attempts desc
| limit 10
```

### 🔹 Brute Force Detection

```sql
stats count(*) as attempts by srcAddr
| filter dstPort = 22 and action = "REJECT"
| sort attempts desc
```

---

## 🧠 Key Learnings

* Understanding of cloud network traffic analysis
* Hands-on experience with AWS logging and monitoring
* Ability to detect suspicious network behavior
* Practical SOC-level investigation skills

---

## 📸 Screenshots

(Add screenshots from your lab here)

---

## 🚀 Conclusion

This project demonstrates practical cloud security monitoring and detection capabilities aligned with real-world SOC analyst responsibilities.![Screenshot 2026-04-05 153045](https://github.com/user-attachments/assets/ad69f785-8d7a-4c54-b656-5e6c0c4398df)
![Screenshot 2026-04-05 152739](https://github.com/user-attachments/assets/814cba3a-63cd-49db-ae84-1b67d9c614c3)
![Screenshot 2026-04-05 142633](https://github.com/user-attachments/assets/839407de-a4a0-49c4-855c-9c333954783c)
![Screenshot 2026-04-05 142038](https://github.com/user-attachments/assets/a162bc95-7a67-4560-b251-2d9970b2a859)
![Screenshot 2026-04-05 141413](https://github.com/user-attachments/assets/17f2df73-6b00-4c6a-b259-d9bfa1c71bf8)
![Screenshot 2026-04-05 141254](https://github.com/user-attachments/assets/df258cf9-66e0-4454-843c-13eecea0da7b)
![Cloudwatch Logs Insights](https://github.com/user-attachments/assets/5669f821-5255-427a-a1a2-cf82b546e768)
