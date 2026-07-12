# PowerShell Basics

## What is PowerShell?

PowerShell is Microsoft's task automation and configuration management framework.

Unlike the traditional Command Prompt (CMD), PowerShell works with **objects** rather than plain text.

PowerShell combines:

- Command-line shell
- Scripting language
- Automation platform

---

# PowerShell Terminology

## Cmdlet

A Cmdlet (Command-let) is a lightweight PowerShell command.

Syntax

Verb-Noun

Examples

```powershell
Get-Process
Get-Service
Get-Help
Set-Location
Stop-Service
```

---

## Pipeline

The pipeline (`|`) sends the output of one command directly to another.

Example

```powershell
Get-Process | Sort-Object CPU
```

Meaning

1. Get running processes.
2. Sort them by CPU usage.

---

## Variables

```powershell
$name = "Chirag"
```

Display

```powershell
$name
```

---

## Comments

Single line

```powershell
# This is a comment
```

Multi-line

```powershell
<#
This is a
multi-line comment.
#>
```

---

# Getting Help

```powershell
Get-Help Get-Service
```

Update help database

```powershell
Update-Help
```

---

# Execution Policy

View policy

```powershell
Get-ExecutionPolicy
```

Allow local scripts

```powershell
Set-ExecutionPolicy RemoteSigned
```

---

# Most Useful Cmdlets

| Cmdlet | Purpose |
|---------|----------|
| Get-Process | Running processes |
| Get-Service | Windows services |
| Get-ComputerInfo | System information |
| Get-NetIPAddress | IP configuration |
| Get-LocalUser | Local users |
| Get-History | Previous commands |
| Clear-Host | Clear console |
| Get-Date | Current date |
