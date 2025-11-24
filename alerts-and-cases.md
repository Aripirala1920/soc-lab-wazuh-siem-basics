# Alert Examples & Basic SOC Analysis

This document contains sample alerts I reviewed in Wazuh and how I analyzed them like an L1 SOC analyst.

---

# 1. Failed Login Attempt (Authentication Failure)

### 🔹 Alert Summary
- **Rule:** Authentication failure  
- **User:** root  
- **Source IP:** 127.0.0.1  
- **Event Type:** Failed login  
- **Severity:** 5 (medium)  

### 🔹 What I checked
- Was it a single failure or repeated?  
- Was it coming from an external IP?  
- Is this expected behaviour?  

### 🔹 Analysis
Repeated failures within seconds may indicate:
- Brute-force attempt  
- Misconfigured script  
- Unauthorized access attempt  

### 🔹 Recommended Action
- Check /var/log/auth.log  
- Verify if the user exists  
- Block or rate-limit suspicious IPs  

---

# 2. Multiple SSH Login Failures

### 🔹 Alert Summary
- **Rule:** sshd repeated failures  
- **Source:** Local VM  
- **Event:** Multiple failed authentication attempts  

### 🔹 Analysis
Patterns like:
- Many rapid failures  
- Attempts on multiple usernames  
…usually indicate brute-force scanning.

### 🔹 Recommended Action
- Review firewall rules  
- Enable fail2ban (Linux brute-force protection)  
- Disable password login & use SSH keys  

---

# 3. System Log Modification Detected

### 🔹 Alert Summary
- **Rule:** System logs changed  
- **Severity:** Medium  

### 🔹 Analysis
Unexpected log modification can indicate:
- User trying to hide activity  
- Misconfigured process  

### 🔹 Recommended Action
- Verify who made the change  
- Restore log file permissions  

---

# 4. Conclusion

This beginner SOC lab helped me understand:
- How alerts appear in SIEM  
- How to read event details  
- How to think like an L1 analyst  
- How to document analysis properly  

Perfect for entry-level cybersecurity roles.
