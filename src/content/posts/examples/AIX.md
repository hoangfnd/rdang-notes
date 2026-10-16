---
title: "AIX Operations Handbook"
description: "Daily operation, troubleshooting and administration notes for IBM AIX."
pubDatetime: 2026-10-16T16:55:12.000+00:00
tags:
  - aix
  - unix
  - infrastructure
  - operations
  - ibm
---

# AIX Operations Handbook

A collection of useful commands, procedures, and troubleshooting notes for daily AIX administration and operations.

---

# System Information

## AIX Version

```bash
oslevel -s
```

Example:

```text
7300-01-02-2320
```

## Hostname

```bash
hostname
```

## Uptime

```bash
uptime
```

## Server Serial Number

```bash
uname -Mu
```

---

# CPU Monitoring

## View CPU Utilization

```bash
topas
```

or

```bash
vmstat 1
```

## CPU Information

```bash
prtconf | grep "Processor"
```

```bash
lparstat -i
```

---

# Memory Monitoring

## Check Memory Usage

```bash
svmon -G
```

## Human Readable Summary

```bash
vmstat -v
```

## Top Memory Consumers

```bash
svmon -P | head
```

---

# Disk Management

## View Filesystems

```bash
df -g
```

## Disk Usage

```bash
du -g /filesystem
```

## List Physical Volumes

```bash
lspv
```

## List Volume Groups

```bash
lsvg
```

## List Logical Volumes

```bash
lsvg -l rootvg
```

---

# Filesystem Expansion

## Check Free Space in Volume Group

```bash
lsvg rootvg
```

## Extend Filesystem

Example:

```bash
chfs -a size=+10G /app
```

Verify:

```bash
df -g /app
```

---

# Network Operations

## Network Interfaces

```bash
ifconfig -a
```

## Route Table

```bash
netstat -rn
```

## Listening Ports

```bash
netstat -an | grep LISTEN
```

## Test Connectivity

```bash
ping hostname
```

```bash
telnet hostname port
```

---

# Process Monitoring

## Top Processes

```bash
topas
```

## Search Process

```bash
ps -ef | grep process_name
```

## Kill Process

```bash
kill -15 PID
```

Force:

```bash
kill -9 PID
```

---

# User Management

## List Users

```bash
lsuser ALL
```

## User Details

```bash
lsuser username
```

## Change Password

```bash
passwd username
```

## Unlock Account

```bash
chuser account_locked=false username
```

---

# 