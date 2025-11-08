---
title: "SOC Investigation 101: Tracing a Suspicious PowerShell Execution"
date: 2025-09-15T11:00:00-06:00
draft: false
description: "A walkthrough of a real-world SOC investigation involving a malicious PowerShell script, from alert to root cause."
author: "Darpan Basnet"
categories: ["SOC Investigation", "Incident Response"]
tags: ["SOC Investigation", "Windows" ]
toc: true
summary: "This post walks through a practical SOC investigation — analyzing PowerShell alerts, correlating events, and validating malicious activity using Elastic Stack and Defender telemetry."
---

In the SOC, not every alert is created equal — but every one tells a story.  
This post breaks down a real-world scenario where a PowerShell-based alert turned into a full investigation.

---

## 🧩 Step 1: The Alert

Elastic triggered an alert titled **“Suspicious PowerShell Download Activity.”**  
The query matched:
```kql
process.name : "powershell.exe" and process.command_line : "*DownloadString*"
