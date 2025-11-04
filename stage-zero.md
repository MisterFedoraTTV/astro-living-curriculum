# Stage 0 — Orientation & System Setup  
*(Raspberry Pi 3 Edition — Extended Plan)*  

## Overview  
This stage establishes your complete learning environment on a Raspberry Pi 3 (B/B+).  
You will learn how to:  
- Operate the Linux command line  
- Install and verify a full Python + Jupyter scientific environment  
- Use Git & GitHub for version control  
- Perform first calculations in Python  
- Understand dimensional analysis and unit consistency  

---

## Lesson 1 — System Preparation & Linux Basics

### 🎯 Objectives  
- Familiarize with Raspberry Pi OS desktop and terminal  
- Learn essential Linux commands  
- Update and secure your system  

### 🧩 Concept Focus  
Command-line workflow · File structure · Permissions · Package management  

### 💻 CLI Steps  

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install build-essential curl git vim nano python3-pip -y
mkdir -p ~/astro_lab/{projects,data,notes}
cd ~/astro_lab
