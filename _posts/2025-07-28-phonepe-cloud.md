---
layout: post
title: Case Study: PhonePe Internal Cloud - Simplified Overview
cover-img: /assets/img/path.jpg
thumbnail-img: /assets/img/thumb.png
share-img: /assets/img/path.jpg
tags: [cloud, case-study]
comments: true
author: Jay Bhanushali
---

# 📡 PhonePe Cloud (PPEC) — Simplified Overview

## 🚀 What is PPEC?

**PPEC (PhonePe Cloud)** is PhonePe’s internal cloud provisioning system. It's like their private version of AWS, designed to fit how their internal teams work.

It helps teams:
- Get new machines (servers)
- Set them up quickly
- Run virtual machines (VMs)
- Manage everything from one place
- Track and audit who does what

---

## 🌱 Why Was PPEC Built?

- Earlier, a few experts handled infrastructure with tribal knowledge.
- As PhonePe scaled, many teams (non-experts too) needed to provision servers.
- PPEC was built to make provisioning **easier**, **safer**, and **more reliable**.

---

## 🧠 Key Design Goals

1. ✅ Single client usable across all regions (with proper authorization)
2. 📜 Auditability and changelogs
3. 🧱 Full lifecycle support: from racking → inventory → provisioning → retiring

---

## ⚙️ Core Workflows

### 🆕 1. New Inventory Handling
- New server boots into **PIOUS** (PhonePe Inventory OS)
- Verifies hardware specs and health
- Promotes healthy machines to a SPARE state
- SPAREs = ready-to-use machines, classified by type

### 🖥 2. Baremetal Provisioning
- SPAREs become **BAREMETALs** (production servers)
- Hardened OS images installed via PIOUS
- Hardware integrity is checked during provisioning

### 💻 3. Virtual Machine Management
- Uses **KVM + libvirt + QEMU**
- VM placement done via **Mesos** (for now)
- Migration planned to a **custom placement algorithm**

---

## 🧰 Interfaces to Use PPEC

### 🖥 PPEC Client (CLI)
- Query assets
- Provision VMs or baremetals
- Manage IPs, networks, regions
- Tag resources
- RBAC (role-based access control)
- Maker-checker system

### 📊 PPEC Dashboard (Web UI)
- Visual view of assets by region
- Filter/search machines
- Generate scoped credentials
- Alerts and logs
- Built-in docs & Swagger

### 📦 PPEC SDK
- Programmatic API access
- Used in automation, monitoring, CI/CD pipelines

---

## ✅ Summary

PPEC is:
- A cloud provisioning system made for **PhonePe’s internal use**
- Tailored to how their teams operate
- Focused on **usability**, **reliability**, and **no unused features**
- Available via **CLI**, **Dashboard**, and **SDK**

It's how PhonePe manages infrastructure **at scale**, safely and efficiently.