# 4. System Administration with PowerShell

---

# Learning Objectives

After completing this chapter, I should be able to:

- Gather system information
- Identify the logged-in user
- Check Windows version
- Monitor disk space
- View installed hotfixes (Windows Updates)
- Check system uptime
- Generate basic system reports

---

# What is System Administration?

System Administration is the process of managing, maintaining, and troubleshooting computer systems.

A System Administrator ensures that computers remain:

- Secure
- Updated
- Reliable
- Available
- Performing efficiently

PowerShell helps automate many of these administrative tasks.

---

# Why Does IT Support Use PowerShell?

Imagine supporting 200 office computers.

Opening Settings on every computer would take hours.

PowerShell can retrieve information from all systems in seconds.

---

# Check Computer Information

## Command

```powershell
Get-ComputerInfo
```

## What it does

Displays detailed information about the current computer.

Information includes:

- Windows Version
- BIOS
- Processor
- RAM
- Time Zone
- Windows Directory
- Device Name
- Manufacturer
- Model

---

## Real World Example

A user calls saying:

> "My laptop is running Windows 10, but I'm not sure which version."

Instead of opening multiple settings pages:

```powershell
Get-ComputerInfo
```

---

💡 Pro Tip

The output is very large.

Filter only the information you need:

```powershell
Get-ComputerInfo | Select-Object WindowsProductName, WindowsVersion
```

---

🧪 Try It Yourself

Run:

```powershell
Get-ComputerInfo
```

Can you find:

- Computer Name
- Windows Version
- BIOS Version
- Manufacturer

---

# Find the Current User

## Command

```powershell
whoami
```

## What it does

Displays the currently logged-in user.

Example output

```
DESKTOP-ABC123\chirag
```

---

## Why is this useful?

When troubleshooting permissions or access issues, it's important to verify which user is currently signed in.

---

🧪 Try It Yourself

Run:

```powershell
whoami
```

Does it match your Windows account?

---

# Find the Computer Name

## Command

```powershell
hostname
```

Example

```
WS-01
```

---

## Why is this useful?

In business environments, every computer has a unique hostname.

Example:

```
FINANCE-PC-12

HR-LAPTOP-05

WS-01
```

Helpdesk technicians often ask for the hostname before beginning remote troubleshooting.

---

# Check System Uptime

## Command

```powershell
(Get-Date) - (gcim Win32_OperatingSystem).LastBootUpTime
```

## What it does

Shows how long the computer has been running since the last restart.

---

## Why is this useful?

Many Windows problems are solved simply by restarting the computer.

Before asking the user to reboot, check the uptime.

---

# View Installed Windows Updates

## Command

```powershell
Get-HotFix
```

## What it does

Displays installed Windows updates.

Example output

```
KB5062554

InstalledOn

Description
```

---

## Real World Example

A user says:

> "The problem started after yesterday's Windows Update."

Use:

```powershell
Get-HotFix
```

to verify recently installed updates.

---

🧪 Try It Yourself

Run:

```powershell
Get-HotFix
```

Can you identify the most recently installed update?

---

# Check Disk Space

## Command

```powershell
Get-PSDrive -PSProvider FileSystem
```

## Example Output

```
Name Used Free

C 120GB 350GB

D 20GB 900GB
```

---

## Why is this useful?

A nearly full drive can cause:

- Slow performance
- Failed Windows Updates
- Application crashes
- Login problems

---

💡 Pro Tip

If the system drive (C:) has less than 10–15% free space, investigate unnecessary files or applications.

---

# View Running Processes

## Command

```powershell
Get-Process
```

## What it does

Lists all running applications and background processes.

Example:

```
chrome

explorer

powershell

svchost
```

---

## Sort by CPU Usage

```powershell
Get-Process | Sort-Object CPU -Descending
```

Useful for identifying applications consuming excessive CPU resources.

---

## Sort by Memory Usage

```powershell
Get-Process | Sort-Object WorkingSet -Descending
```

Useful for finding memory-intensive applications.

---

🧪 Try It Yourself

Which application is using the most CPU right now?

Which application is using the most RAM?

---

# View Running Services

## Command

```powershell
Get-Service
```

## What it does

Lists all Windows services.

---

Running services only

```powershell
Get-Service |
Where-Object Status -eq Running
```

---

Stopped services only

```powershell
Get-Service |
Where-Object Status -eq Stopped
```

---

## Real World Example

The user cannot print.

Check whether the Print Spooler service is running.

```powershell
Get-Service Spooler
```

---

# Common Administrative Commands

| Command | Purpose |
|---------|----------|
| Get-ComputerInfo | System information |
| hostname | Computer name |
| whoami | Current user |
| Get-HotFix | Installed Windows updates |
| Get-Process | Running applications |
| Get-Service | Windows services |
| Get-PSDrive | Disk usage |

---

# Mini Lab

A user reports:

- Computer is slow
- Printer is not working
- Windows was updated yesterday

Using only PowerShell:

1. Find the computer name.

2. Find the current user.

3. Check installed updates.

4. Verify the Print Spooler service.

5. Check available disk space.

6. List the top CPU-consuming processes.

Think about which commands you would use before scrolling down.

---

## Possible Solution

```powershell
hostname

whoami

Get-HotFix

Get-Service Spooler

Get-PSDrive -PSProvider FileSystem

Get-Process | Sort-Object CPU -Descending
```

---

# Common Beginner Mistakes

❌ Running commands without understanding their output.

❌ Ignoring system uptime.

❌ Forgetting to check available disk space.

❌ Looking only at Task Manager instead of PowerShell.

---

# Best Practices

✔ Verify information before making changes.

✔ Document commands used during troubleshooting.

✔ Prefer built-in PowerShell cmdlets over third-party tools when possible.

✔ Use PowerShell to gather evidence before attempting fixes.

---

# Quick Revision

✅ System Administration is maintaining and troubleshooting computers.

✅ `Get-ComputerInfo` displays detailed system information.

✅ `hostname` shows the computer name.

✅ `whoami` identifies the logged-in user.

✅ `Get-HotFix` lists installed Windows updates.

✅ `Get-Process` displays running processes.

✅ `Get-Service` displays Windows services.

✅ `Get-PSDrive` checks available disk space.

---

# Interview Questions

1. What information does `Get-ComputerInfo` provide?

2. Why is `hostname` important in an enterprise environment?

3. What does `Get-HotFix` display?

4. How would you identify the application using the most CPU?

5. Why should you check disk space before troubleshooting performance issues?

6. A user says, "My printer isn't working." Which PowerShell command would you run first to check the Print Spooler service?
