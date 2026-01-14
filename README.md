# SSH Security Learning

This repository contains notes, commands, logs, attacks, and defenses related to **SSH (Secure Shell)** from a security and SOC perspective.

## Purpose
- Learn SSH fundamentals
- Understand real-world SSH attacks
- Analyze SSH logs
- Practice detection and defense techniques

## Topics Covered
- What is SSH
- How SSH works
- SSH authentication methods
- Common SSH attacks
  - Brute force
  - Password spraying
  - Credential abuse
- SSH logs analysis
- SOC detection techniques
- SSH hardening and defense

## Important Files & Paths
- SSH config  
  - `/etc/ssh/sshd_config`
- SSH logs  
  - `/var/log/auth.log`

## Common SSH Commands
```bash
ssh user@ip
ssh -i key.pem user@ip
systemctl status ssh
journalctl -u ssh
