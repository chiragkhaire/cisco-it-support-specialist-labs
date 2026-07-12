# Sample Ticket Analysis

## Ticket ID

INC-0001

---

### Issue

User cannot connect to the office Wi-Fi.

---

### Symptoms

- Wi-Fi connected
- No internet access
- Other users unaffected

---

### Investigation

- Verified SSID
- Checked IP configuration
- Renewed DHCP lease
- Restarted wireless adapter

---

### Root Cause

Corrupted DHCP lease.

---

### Resolution

Released and renewed IP address.

Commands used:

```cmd
ipconfig /release
ipconfig /renew
```

---

### Verification

- Internet working
- Email accessible
- Teams connected

---

### Ticket Status

Closed

---

### Lessons Learned

Always verify network configuration before escalating the issue.
