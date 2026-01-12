# Day 1 – SSH Basics

## What I learned
- SSH is a secure remote access protocol.
- It follows a client-server model.
- Used to manage Linux servers remotely.

## Authentication Methods
- Password-based authentication
- Key-based authentication (recommended)

## Security Perspective
- SSH gives direct system access, so attackers target it.
- Brute force attacks happen when weak passwords are used.

## Questions
- How do SOC teams detect SSH brute force attacks?
# How SOC Teams Detect SSH Brute Force Attacks

## Log Monitoring
SOC teams primarily monitor SSH authentication logs on Linux systems.

Common log file:
- `/var/log/auth.log`

Typical brute force log entries:


Indicators:
- Multiple failed login attempts
- Same source IP repeating
- Attempts on multiple usernames

---

## Threshold-Based Detection
SOC teams configure thresholds in SIEM tools.

Examples:
- More than 5 failed SSH logins in 1 minute
- More than 20 failed attempts in 5 minutes
- Multiple usernames from the same IP address

When thresholds are exceeded, an alert is generated.

---

## Behavioral Pattern Analysis
SOC analysts look for non-human behavior such as:
- Very fast login attempts
- Sequential username attempts (root, admin, test, ubuntu)
- Only failed attempts without success

This pattern usually indicates automation.

---

## Geo-Location Anomalies
Detection includes checking:
- SSH attempts from unexpected countries
- Access attempts outside normal business locations

Example:
- Server used only in India
- SSH attempts from multiple foreign IPs

---

## SIEM Correlation
SIEM tools correlate multiple data points:
- Source IP
- Username
- Host
- Time window

This converts thousands of log entries into a single actionable alert.

---

## Successful Login After Failures
High-risk scenario:
- Multiple failed login attempts
- Followed by a successful login

This may indicate credential compromise and is escalated immediately.

---

## SOC Summary
SOC teams detect SSH brute force attacks by correlating failed authentication logs using thresholds, behavioral patterns, and anomaly detection within SIEM platforms.
