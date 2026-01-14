# Day 2 – SSH Attacks & Logs (SOC Basics)

## 1. SSH Authentication Types

### 1.1 Password-based Authentication
- User connects using username and password
- Example:
  ssh user@server_ip
- This method is weak
- Easily targeted by brute force attacks

### 1.2 Key-based Authentication
- Uses a public and private key pair
- More secure than passwords
- Preferred by Tier-1 companies

Key files:
- id_rsa → private key (must be kept secret)
- id_rsa.pub → public key (stored on server)

---

## 2. SSH Brute Force Attack

### What is SSH Brute Force?
- An attack where an attacker tries many username and password combinations
- Goal is to gain unauthorized access to the server

### Common Targeted Usernames
- root
- admin
- ubuntu
- test

### Attack Flow
1. Attacker scans the internet for servers with port 22 open
2. Tries common usernames
3. Tries thousands of passwords
4. If successful, attacker gains full remote access

### Why SSH is Targeted
- SSH gives direct shell access
- Many servers expose SSH to the internet
- Weak passwords are common

---

## 3. SSH Logs (SOC Perspective)

### Log File Location (Linux)
- Ubuntu / Debian:
  /var/log/auth.log

### Important SSH Log Events
- Failed password
- Accepted password
- Invalid user
- Connection closed

### Example Log Entry
Failed password for invalid user admin from 192.168.1.10 port 54321 ssh2

This log tells:
- Username tried: admin
- Source IP: 192.168.1.10
- Result: Authentication failed

---

## 4. Why SSH Logs Matter in SOC
- Used to detect brute force attacks
- Helps identify malicious IP addresses
- Used to create alerts and incident reports

---

## 5. Day 2 Summary
- Learned SSH authentication types
- Understood SSH brute force attacks
- Identified SSH log locations
- Learned key log indicators for SOC monitoring

## Command Syntax Meaning (Only Meaning, No Extra Explanation)

**Command:**
sudo journalctl -u ssh

### Word-by-word meaning:

**sudo**  
Admin permission  

Required to read system logs

**journalctl**  
Command used to view systemd logs  

*(read-only, does not make any changes)*

**-u**  
Unit option  

Shows only a specific service

**ssh**  
SSH service name  

*(short form of ssh.service)*

---

### Full meaning (one line):

“Show all system logs related to the SSH service with admin permission”

---

### Important (syntax point):

- This command does **not** start or stop the service  
- It only shows **history (logs)**

---

If you want another command syntax explained,  
just paste the command —  
I will explain it in the same format.

---

### Clarification:

**Correct. ✅**

On your current system:

- No SSH login attempts were made  
- So there is **no history**

That’s why `journalctl -u ssh` did not show login logs.

**One line:**  
If there is no history, nothing will be shown.
