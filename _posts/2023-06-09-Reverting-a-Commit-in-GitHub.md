---
title: Reverting a Commit in GitHub
date: 2023-06-09 15:09:00 +09:00
categories: [Git, Commands]
tags: [git, github, commands] # TAG names should always be lowercase
---

# Reverting a Commit in GitHub

How to revert a commit and force push in a local repository to remove commit history.

The commit history will also be deleted.

```
 git reset --hard <commit id>
 git push -f origin main
```
