---
title: "Hello, world"
description: "A placeholder post to check that the blog works."
pubDate: 2026-10-19
tags: ["meta"]
draft: false
---

This is a placeholder post. Replace it with something real.

## What to expect

Notes on things I build after the main quest:

- Microsoft 365 and Azure tooling
- PowerShell and Graph API snippets
- Small experiments that did not need a whole project

Source for everything lives on [GitHub](https://github.com/RobinpZA).

## A code sample

```powershell
Connect-MgGraph -Scopes 'User.Read.All'
Get-MgUser -Top 5 | Select-Object DisplayName, UserPrincipalName
```
