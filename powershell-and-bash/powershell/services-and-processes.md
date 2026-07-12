# 6. Services & Processes

---

# Learning Objectives

After completing this chapter, I should be able to:

- Understand the difference between a process and a service
- View running processes
- View Windows services
- Start, stop, and restart services
- End unresponsive applications
- Monitor CPU and memory usage
- Troubleshoot common Windows service issues

---

# What is a Process?

A **process** is a running instance of a program.

Whenever you open an application, Windows creates a process for it.

Examples:

- Google Chrome
- Microsoft Word
- Discord
- Explorer
- Notepad

Every open application is running as one or more processes.

---

# What is a Service?

A **service** is a background program that runs without the user opening it.

Services usually start automatically when Windows boots.

Examples:

- Windows Update
- Print Spooler
- DHCP Client
- DNS Client
- Windows Defender
- Remote Desktop Services

Unlike applications, services usually do not have a visible window.

---

# Process vs Service

| Process | Service |
|----------|----------|
| Started by a user or application | Usually starts with Windows |
| Often has a visible window | Runs in the background |
| Can usually be closed safely | Stopping may affect system functionality |
| Examples: Chrome, Word | Examples: DHCP, Print Spooler |

---

# View Running Processes

## Command

```powershell
Get-Process
```

## What it does

Displays all running processes on the computer.

Example Output

```
Name

CPU

Id

WorkingSet

chrome

123

4528

250 MB
```

---

## Why is this useful?

Use this command to:

- Find applications consuming high CPU
- Check if a program is running
- Identify unresponsive applications
- Monitor system performance

---

🧪 Try It Yourself

Run:

```powershell
Get-Process
```

Can you find:

- Chrome
- Explorer
- PowerShell

---

# Sort Processes by CPU Usage

```powershell
Get-Process |
Sort-Object CPU -Descending
```

The process at the top has used the most CPU time.

---

# Sort Processes by Memory Usage

```powershell
Get-Process |
Sort-Object WorkingSet -Descending
```

Useful when a computer feels slow because of high RAM usage.

---

💡 Pro Tip

High memory usage does not always mean a process is faulty.

Always investigate before ending a process.

---

# Stop a Process

Sometimes an application freezes and stops responding.

PowerShell can terminate it.

## Syntax

```powershell
Stop-Process -Name notepad
```

or

```powershell
Stop-Process -Id 4528
```

---

⚠️ Warning

Only stop processes you understand.

Ending important Windows processes can cause system instability.

---

# View Windows Services

## Command

```powershell
Get-Service
```

Displays all Windows services.

Example Output

```
Status

Name

DisplayName

Running

Spooler

Print Spooler
```

---

# Running Services

```powershell
Get-Service |
Where-Object Status -eq Running
```

---

# Stopped Services

```powershell
Get-Service |
Where-Object Status -eq Stopped
```

---

# View a Specific Service

Example:

```powershell
Get-Service Spooler
```

Output:

```
Status

Running

Name

Spooler
```

---

# Start a Service

```powershell
Start-Service Spooler
```

Starts the Print Spooler service if it is stopped.

---

# Stop a Service

```powershell
Stop-Service Spooler
```

Stops the service.

Administrator privileges may be required.

---

# Restart a Service

```powershell
Restart-Service Spooler
```

This is commonly used in IT support.

Instead of restarting the entire computer, restarting one service can often solve the problem.

---

# Common Windows Services

| Service | Purpose |
|----------|----------|
| Print Spooler | Printing |
| Windows Update | Updates Windows |
| DHCP Client | Obtains IP Address |
| DNS Client | Resolves domain names |
| Windows Defender | Antivirus protection |
| Remote Desktop Services | Remote access |
| Windows Time | Time synchronization |

---

# Real IT Support Scenario 1

## Ticket

> "My printer isn't printing."

### Investigation

Check the Print Spooler service.

```powershell
Get-Service Spooler
```

If stopped:

```powershell
Restart-Service Spooler
```

Verify printing again.

---

# Real IT Support Scenario 2

## Ticket

> "Google Chrome has frozen."

### Investigation

Locate the process.

```powershell
Get-Process chrome
```

If necessary:

```powershell
Stop-Process -Name chrome
```

Ask the user to reopen Chrome.

---

# Mini Lab

A user reports:

- Computer is slow
- Chrome keeps freezing
- Printer is not responding

Using only PowerShell:

1. View running processes.

2. Find the processes using the most CPU.

3. Find the processes using the most memory.

4. Verify the Print Spooler service.

5. Restart the Print Spooler service.

Think about which commands you would use before checking below.

---

## Possible Solution

```powershell
Get-Process

Get-Process |
Sort-Object CPU -Descending

Get-Process |
Sort-Object WorkingSet -Descending

Get-Service Spooler

Restart-Service Spooler
```

---

# Common Beginner Mistakes

❌ Ending random processes without understanding their purpose.

❌ Stopping critical Windows services.

❌ Restarting the entire computer when only one service needs restarting.

❌ Assuming every stopped service is a problem.

---

# Best Practices

✔ Identify the issue before stopping processes.

✔ Restart services instead of rebooting the computer when appropriate.

✔ Document every administrative action taken.

✔ Verify that the issue is resolved after restarting a service.

---

# Quick Revision

✅ A process is a running application.

✅ A service runs in the background.

✅ `Get-Process` displays running processes.

✅ `Stop-Process` terminates a process.

✅ `Get-Service` displays Windows services.

✅ `Start-Service` starts a service.

✅ `Stop-Service` stops a service.

✅ `Restart-Service` restarts a service.

---

# Interview Questions

1. What is the difference between a process and a service?

2. Which command lists running processes?

3. Which command lists Windows services?

4. When would you use `Restart-Service`?

5. Why shouldn't you stop unknown processes or services?

6. A user's printer isn't working. Which PowerShell commands would you use to investigate the issue?
