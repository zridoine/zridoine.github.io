---
title: Forcing a Pull in the Local Repository
date: 2023-06-09 15:15:40 +09:00
categories: [Git, Commands]
tags: [git, github] # TAG names should always be lowercase
---

# Forcing a Pull in the Local Repository

Overwriting the code in the local repository with whatever code is in the GitHub repository.

```
git fetch --all
git reset --hard origin/main
git pull origin main
```
