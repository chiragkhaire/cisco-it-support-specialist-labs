# Helpdesk Case Studies

---

# Case 1 — User Cannot Connect to Wi-Fi

## Issue

The user reports that the laptop is connected to Wi-Fi but has no internet access.

### Investigation

- Verified Wi-Fi connection
- Checked IP configuration
- Confirmed router operational
- Other users unaffected

### Commands Used

```cmd
ipconfig
ping 8.8.8.8
ipconfig /release
ipconfig /renew
```

### Root Cause

Corrupted DHCP lease.

### Resolution

Released and renewed IP configuration.

### Verification

- Internet access restored
- Browser working
- Microsoft Teams connected

---

# Case 2 — Windows Running Slowly

## Investigation

- Checked Task Manager
- Startup applications reviewed
- Storage utilization verified
- Malware scan completed

### Root Cause

Multiple startup applications and low available disk space.

### Resolution

- Disabled unnecessary startup applications
- Removed temporary files
- Performed Windows Update

### Verification

Boot time improved and system performance normalized.

---

# Case 3 — Printer Offline

## Investigation

- Checked printer power
- Verified USB connection
- Restarted Print Spooler
- Printed test page

### Root Cause

Print Spooler service stopped.

### Resolution

Restarted Print Spooler service.

### Verification

Printer successfully printed test page.

---

# Case 4 — User Forgot Password

## Investigation

Identity verified.

### Resolution

Password reset according to organizational policy.

### Verification

User successfully logged into Windows.

---

# Case 5 — Blue Screen of Death

## Investigation

- Event Viewer checked
- Windows Memory Diagnostic executed
- Driver updates reviewed

### Root Cause

Faulty graphics driver.

### Resolution

Installed latest stable driver.

### Verification

No further BSOD events observed.

---

# Case 6 — VPN Connection Failure

## Investigation

- Internet connectivity verified
- VPN credentials validated
- DNS resolution tested

### Root Cause

Expired VPN credentials.

### Resolution

Updated credentials and reconnected.

### Verification

Remote resources successfully accessible.

---

# Case 7 — Email Not Sending

## Investigation

- Internet working
- SMTP settings reviewed
- Mailbox storage checked

### Root Cause

Mailbox quota exceeded.

### Resolution

Archived old emails.

### Verification

Emails sending normally.

---

# Case 8 — Computer Will Not Boot

## Investigation

- Power supply checked
- RAM reseated
- BIOS accessed

### Root Cause

Loose memory module.

### Resolution

Reseated RAM.

### Verification

System booted successfully.

---

# Case 9 — Slow Wi-Fi

## Investigation

- Signal strength checked
- Driver updated
- Router restarted

### Root Cause

Outdated wireless driver.

### Resolution

Installed latest driver.

### Verification

Network speed returned to expected levels.

---

# Case 10 — Malware Detection

## Investigation

Antivirus reported suspicious executable.

### Resolution

- Isolated device
- Removed malicious files
- Updated antivirus
- Full system scan completed

### Verification

No threats detected after rescanning.

---
