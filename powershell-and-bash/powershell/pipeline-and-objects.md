# 3. Objects & The PowerShell Pipeline

---

# Learning Objectives

After completing this chapter, I should be able to:

- Understand what an object is
- Explain why PowerShell uses objects instead of plain text
- Understand the PowerShell Pipeline (`|`)
- Pass objects between commands
- Filter, sort, and select information
- Use the pipeline in real-world IT support scenarios

---

# What is an Object?

An object is a collection of related information.

Think of an object like a student ID card.

Instead of only showing a student's name, it stores multiple pieces of information.

Example:

```
Student

Name : Chirag

Age : 24

Roll No : 17

Class : BCA

Phone : 9876543210
```

This entire record is **one object**.

---

# Why Objects Matter

Traditional Command Prompt (CMD) mostly works with plain text.

Example:

```
Running
```

PowerShell works with structured objects.

Instead of only returning:

```
Running
```

PowerShell returns something like:

```
Name

Status

Display Name

Service Type

Start Type

Description
```

Every one of these is a property of the object.

---

# Real World Example

Imagine a helpdesk ticket:

> "Find every stopped Windows service."

CMD would give lots of text that you must manually search.

PowerShell understands each service as an object.

So you can simply ask:

```powershell
Get-Service
```

Every service returned has information like:

- Name
- Status
- DisplayName
- ServiceType

PowerShell can work with that information directly.

---

# Properties

Properties describe an object.

Example:

A Windows Service object has properties such as:

| Property | Meaning |
|----------|---------|
| Name | Internal service name |
| DisplayName | Friendly name |
| Status | Running or Stopped |
| ServiceType | Windows Service type |

---

# Methods

Objects can also perform actions.

These actions are called **Methods**.

Example:

Think of a car.

Properties

- Brand
- Model
- Colour
- Speed

Methods

- Start()
- Stop()
- Accelerate()

Objects contain both information and actions.

---

# What is the Pipeline?

The pipeline is represented by:

```
|
```

Read it as:

> "Pass the output of one command into another command."

Think of it as a conveyor belt in a factory.

```
Command A

↓

Pipeline

↓

Command B

↓

Result
```

---

# Basic Example

```powershell
Get-Service | Sort-Object Status
```

Step 1

Get every Windows service.

↓

Step 2

Pass them to Sort-Object.

↓

Step 3

Sort by Status.

---

# Another Example

```powershell
Get-Process | Sort-Object CPU
```

Meaning

1. Get all running processes.

2. Send them through the pipeline.

3. Sort them by CPU usage.

---

# Selecting Specific Information

Sometimes you don't want every property.

Use:

```powershell
Select-Object
```

Example

```powershell
Get-Service | Select-Object Name, Status
```

Output

```
Name                Status

Spooler             Running

Dhcp                Running

WinDefend           Running
```

---

# Filtering Results

Use

```powershell
Where-Object
```

Example

```powershell
Get-Service |
Where-Object Status -eq Running
```

Meaning

Show only running services.

---

Stopped services

```powershell
Get-Service |
Where-Object Status -eq Stopped
```

---

# Sorting Results

```powershell
Get-Process |
Sort-Object CPU
```

Highest CPU first

```powershell
Get-Process |
Sort-Object CPU -Descending
```

---

# Counting Objects

```powershell
Get-Process |
Measure-Object
```

Example output

```
Count : 182
```

Useful for quickly counting:

- Processes
- Services
- Files
- Users

---

# Discovering Object Properties

One of the most important commands in PowerShell:

```powershell
Get-Service | Get-Member
```

This shows:

- Properties
- Methods
- Object Type

Whenever you're unsure what information an object contains, use:

```powershell
Get-Member
```

---

# Complete Example

```powershell
Get-Service |
Where-Object Status -eq Running |
Sort-Object DisplayName |
Select-Object Name, Status
```

Read it from left to right.

1. Get every service.

↓

2. Keep only running services.

↓

3. Sort alphabetically.

↓

4. Display only Name and Status.

---

# Real IT Support Example

Ticket:

> "A user reports printing is not working."

First check the Print Spooler service.

```powershell
Get-Service |
Where-Object Name -eq Spooler
```

Need only its status?

```powershell
Get-Service |
Where-Object Name -eq Spooler |
Select-Object Name, Status
```

Need to restart it?

```powershell
Restart-Service Spooler
```

---

# Common Beginner Mistakes

❌ Thinking PowerShell returns plain text.

❌ Forgetting the pipeline passes **objects**.

❌ Not using Get-Member.

❌ Trying to memorize every property.

---

# Best Practices

✔ Read pipeline commands from left to right.

✔ Use Select-Object to reduce unnecessary output.

✔ Use Where-Object instead of manually searching.

✔ Use Sort-Object to organize results.

✔ Explore every new object using Get-Member.

---

# Quick Revision

✅ Objects contain data.

✅ Properties describe objects.

✅ Methods perform actions.

✅ The pipeline passes objects between commands.

✅ Select-Object chooses specific properties.

✅ Where-Object filters objects.

✅ Sort-Object sorts objects.

✅ Measure-Object counts objects.

---

# Interview Questions

### 1. What is an object in PowerShell?

### 2. Why does PowerShell use objects instead of text?

### 3. What does the pipeline (`|`) do?

### 4. What is the purpose of Select-Object?

### 5. What does Where-Object do?

### 6. What is Get-Member used for?

### 7. Explain this command:

```powershell
Get-Process | Sort-Object CPU
```

### 8. Explain this command:

```powershell
Get-Service | Where-Object Status -eq Running
```
