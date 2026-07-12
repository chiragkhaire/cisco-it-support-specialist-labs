# 2. Basic PowerShell Commands

---

# Learning Objectives

After completing this chapter, I should be able to:

- Navigate PowerShell confidently
- Find available commands
- Understand command syntax
- Read command documentation
- Discover command parameters
- Use aliases
- Recall command history
- Improve productivity using tab completion

---

# Understanding Command Syntax

Most PowerShell commands follow the same structure.

```
Verb-Noun
```

Examples:

```powershell
Get-Process
Get-Service
Get-Date
Get-Help
Get-Command
```

Think of it like English.

```
Get = Retrieve

Process = Running processes

Get-Process
↓

Retrieve running processes.
```

---

# Get-Help

## What is it?

Displays documentation for a PowerShell command.

This should be your **first stop** whenever you don't know how to use a command.

---

## Syntax

```powershell
Get-Help <CommandName>
```

---

## Examples

```powershell
Get-Help Get-Service
```

```powershell
Get-Help Get-Process
```

Detailed help

```powershell
Get-Help Get-Service -Detailed
```

Examples only

```powershell
Get-Help Get-Service -Examples
```

Online documentation

```powershell
Get-Help Get-Service -Online
```

---

## Real IT Support Example

A ticket asks you to restart a Windows service.

You don't remember how **Restart-Service** works.

Instead of searching Google:

```powershell
Get-Help Restart-Service
```

---

# Get-Command

## What is it?

Lists all available PowerShell commands.

Think of it as a search engine for PowerShell.

---

## Syntax

```powershell
Get-Command
```

---

## Find commands related to networking

```powershell
Get-Command *Net*
```

Find commands related to services

```powershell
Get-Command *Service*
```

Find commands related to processes

```powershell
Get-Command *Process*
```

---

## Why is it useful?

Suppose you know there must be a command related to printers.

Search for it:

```powershell
Get-Command *Print*
```

PowerShell finds matching cmdlets.

---

# Get-Member

## What is it?

Shows everything an object contains.

Remember:

PowerShell works with **objects**, not plain text.

Objects contain:

- Properties
- Methods

---

## Syntax

```powershell
Get-Process | Get-Member
```

---

## Example

```powershell
Get-Service | Get-Member
```

You'll discover properties like:

- Name
- Status
- DisplayName

This is extremely useful when writing scripts.

---

# Get-Alias

## What is an Alias?

An alias is a shortcut for a command.

Example:

Instead of typing

```powershell
Get-ChildItem
```

you can type

```powershell
dir
```

Both do the same thing.

---

## View all aliases

```powershell
Get-Alias
```

---

## Find an alias

```powershell
Get-Alias dir
```

---

## Common Aliases

| Alias | Actual Command |
|--------|----------------|
| dir | Get-ChildItem |
| ls | Get-ChildItem |
| cd | Set-Location |
| pwd | Get-Location |
| cls | Clear-Host |
| cat | Get-Content |

---

# Clear-Host

Clears the PowerShell screen.

Shortcut:

```powershell
cls
```

---

# Get-History

Displays commands executed during the current PowerShell session.

```powershell
Get-History
```

Example output

```
1 Get-Service

2 Get-Date

3 Get-Process
```

---

# Invoke-History

Runs a command from history.

Example

```powershell
Invoke-History 2
```

This executes command number 2 again.

---

# Tab Completion

PowerShell supports intelligent auto-completion.

Example

Type

```powershell
Get-Pro
```

Press

```
TAB
```

PowerShell completes it to

```powershell
Get-Process
```

This saves time and reduces typing mistakes.

---

# Wildcards

PowerShell supports wildcard searches.

```
*
```

means

"Anything"

Example

```powershell
Get-Command *Service*
```

Finds every command containing

```
Service
```

---

# Updating Help Files

Some help files are not installed by default.

Download them:

```powershell
Update-Help
```

Administrator privileges may be required.

---

# Common Beginner Mistakes

❌ Memorizing commands instead of learning how to find them.

❌ Ignoring Get-Help.

❌ Forgetting TAB completion.

❌ Assuming CMD and PowerShell commands are identical.

---

# Best Practices

✔ Use **Get-Help** before searching online.

✔ Use **Get-Command** whenever you don't know a command name.

✔ Press **TAB** instead of typing long commands.

✔ Learn official cmdlet names instead of relying only on aliases.

✔ Use **Get-Member** whenever you need to understand an object's properties.

---

# Quick Revision

✅ PowerShell commands follow the Verb-Noun format.

✅ Get-Help displays command documentation.

✅ Get-Command searches available commands.

✅ Get-Member explores objects.

✅ Get-Alias lists shortcuts.

✅ Get-History shows previously executed commands.

✅ Tab completion speeds up your work.

---

# Interview Questions

### 1. What does Get-Help do?

### 2. How can you search for PowerShell commands?

### 3. What is an alias?

### 4. Why is Get-Member important?

### 5. What is the purpose of TAB completion?

### 6. What is the difference between Get-Command and Get-Help?

### 7. Why should IT Support Engineers use Get-Help before searching online?
