---
title: "How to set username and email for a specific project"
date: 2025-02-22T14:00:00+07:00
draft: false
tags: ["git", "project", "freelancer"]
categories: ["blog"]
description: "How to optimize a Spring Boot Application to Handle 1M Requests/Second"
weight: 1
ShowToc: true
---
You can set a different Git username and email for a specific project by configuring them locally within the project's repository.
Here's how:

## 1️⃣ Navigate to Your Project Folder

```bash
cd /path/to/your/hugo-blog
```

## 2️⃣ Set Local Git Username & Email

Run the following commands inside your project folder:

```bash
git config user.name "Your Name"
git config user.email "your-email@example.com"
```

## 3️⃣ Verify the Configuration

To check if it’s set correctly:

```bash
git config --local user.name
git config --local user.email
```
This will apply only to this repository, leaving your global Git settings untouched.

## Optional: Check Global vs. Local Configurations

- Global Config (applies to all repos):

```bash
git config --global user.name
git config --global user.email
```

- Local Config (specific to this repo):
```bash
git config --local --list
```
