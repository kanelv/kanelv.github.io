---
title: "2 Ways to Create and Push a Repository on GitHub via Command Line"
date: 2025-03-09T23:00:00+07:00
draft: false
tags: ["git", "repository", "new", "existing"]
categories: ["blog"]
description: "2 Ways to Create and Push a Repository on GitHub via Command Line"
weight: 1
# ShowToc: true
---

## 1. create a new repository on the command line

```bash
echo "# test" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/kanelv/test.git
git push -u origin main
```
## 2. push an existing repository from the command line

```bash
git remote add origin https://github.com/kanelv/test.git
git branch -M main
git push -u origin main
```
