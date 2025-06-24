# 🔐 Secure App Config with AWS KMS & Secrets Manager

This project demonstrates how to securely store and retrieve sensitive application configuration such as API keys, database credentials, etc., using **AWS KMS (Key Management Service)** and **AWS Secrets Manager**.

---

## 📁 Folder Overview

- `kms/`: Contains encryption and decryption example using KMS
- `secrets-manager/`: Contains secrets usage with AWS CLI
- `cloudshell/`: Screenshot of CloudShell terminal used for commands

---

## 🛠 Technologies Used

- **AWS KMS** for encryption and decryption
- **AWS Secrets Manager** for managing secrets
- **AWS CloudShell** for CLI practice

---

## 🔐 KMS: Encryption & Decryption Demo

### 1. Create a Symmetric KMS Key  
✅ Go to **KMS Console** → Create key  
→ Name: `bank-app-key`  
→ Type: Symmetric  
→ Usage: Encrypt and decrypt  

📸 Screenshot:  
![KMS Create Review](kms/screenshots/kms-create-review.png)

---

### 2. Encrypt using AWS CloudShell CLI

```bash
echo "BANK_API=abc123secure" > config.txt

aws kms encrypt \
  --key-id alias/bank-app-key \
  --plaintext fileb://config.txt \
  --output text \
  --query CiphertextBlob | base64 --decode > encrypted-config.txt
