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

### **Exercise**
Run each command and note what happens, then explore the uses of each

pwd
ls -lha
whoami
uname -a

### **Checkpoint**
Reflect on the utilities learned and common uses:

-Can navigate directories (cd, ls, pwd)
-Understands sudo and package installation
-Folder structure ~/astro_lab created successfully

### Lesson 2 - Python and JupyterLab Setup

### Objectives
- Intsall Python packages for scientific work
- Launch and connect to JupyterLab from another device

### Required Tools
python3, pip, venv, jupyterlab, numpy, matplotlib, pandas, sympy

## CLI Steps
sudo apt install python3-venv -y
python3 -m venv ~/astro_env
source ~/astro_env/bin/activate
pip install --upgrade pip
pip install numpy scipy sympy matplotlib pandas jupyterlab
**Note:** if you keep getting an "Externally managed" error, you may need to restart your terminal or use an alternative pip option, such as pipx.

Launch Jupyter
jupyter lab --no-browser --ip=0.0.0.0
Access via browser on another device: http://<Pi_IP>:8888
**Note:** Running Jupyter environments without modifiers will open them in a browser.

##Notebook Test

Create system_check.ipynb and run:

import numpy as np, matplotlib.pyplot as plt
print("Environment check OK")
x = np.linspace(0, 2*np.pi, 100)
plt.plot(x, np.sin(x))
plt.title("First Plot on Raspberry Pi 3")
plt.show()

##Checkpoint
- JupyterLab opens and can execute Python code
- Libraries import successfully
- Understand the purpose of virtual environments

##Lesson 3 - Version Control & GitHub Workflow

##Objectives
- Initialize a local Git repository
- Create a GitHub account and connect via SSH
- Commit and push first notebook

##Required Tools
git, GitHub account

##CLI Steps
sudo apt install git -y
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
ssh-keygen -t ed25519 -C "your@email.com"
cat ~/.ssh/id_ed25519.pub

Copy the key to **GitHub>Settings>SSH Keys>Add New**

Initialize repo:
cd ~/astro_lab
git init
git add .
git commit -m "Initial commit – Stage 0 setup"
git remote add origin git@github.com:<username>/astro-living-curriculum.git
git push -u origin master

##Checkpoint
- Repository visible on GitHub
- Understand add/commit/push cycle
- SSH authentication configured correctly

##**Lesson 4 - Scientific Computing Fundamentals**

##Objectives
- Learn numeric arrays and plotting basics
- Perform reproducible calculations

##Concept Focus

Numpy arrays, Basic plotting, Units and scalimg

##Jupyter Example

import numpy as np
import matplotlib.pyplot as plt

t = np.linspace(0, 10, 200)
x = 0.5 * 9.81 * t**2
plt.plot(t, x)
plt.xlabel("Time (s)")
plt.ylabel("Distance (m)")
plt.title("Free Fall Simulation – x = ½gt²")
plt.show()

##Checkpoint
- Understand NumPy array creation
- Produce labeled plots
- Save notebook in projects/

##**Lesson 5 - Dimensional Analysis & "Hello Universe" Project**

##Objectives
- Apply dimensional consistency to equations
- Run a basic astrophysical computation

##Concept Focus
Units - Scaling - Dimensional analysis - Verification

##Project Code
# Hello, Universe – Kepler's 3rd Law demo
import numpy as np

G = 6.674e-11
M_sun = 1.989e30
a = 1.496e11   # 1 AU (m)

T = 2 * np.pi * np.sqrt(a**3 / (G * M_sun))
print(f"Earth orbital period ≈ {T/86400:.2f} days")

##Reflection
- Why must G, M, and a be consistent?
- How could the simulation fail numerically on small timesteps?
- How does dimensional analysis prevent physical mistakes?

##Checkpoint
- Runs the project successfully
- Explains variable units
- Commits the final notebook to GitHub


**END OF LESSON ZERO**

_Congratulations on finishing the introductory stage! For some, this is elementary knowledge and could be done FAR more efficiently overall, for others it's still absolute gibberish. Both types of people are right, that's the beauty of programming! You can equate coding and programming to learning a second language, and as such you shouldn't feel discouraged if you don't get it immediately. Take your time and don't be afraid to look up answers to the questions you have. I'll try to refrain from using Google as a verb, but you can absolutely treat it like one on your learning journey!

For the former camp of people who find this course poorly made and unoptimized, you're absolutely right: formatting inconsistencies everywhere, posiibly subpar commands galore, simplified uses for extremely useful and powerful tools. I'm not a teacher my guy, I'm taking this course as well. I am actively researching the stages as I build them, learning the concepts on the fly. To that end, I strongly request you help build it! Message me with a little bit about yourself, your background, your gripes with the course, and suggestions for improvement. Please forgive me if I'm a smidge defensive though, I've had so many people telling me that my HOBBY project is useless, boring, or horribly done without any helpful input and it's gotten to me a bit and I apologize if I come off as rude because of it at any point.

With that unnecessarily long outro done, let's move on to stage one, where we will go over the building blocks and baby steps of the math the eventually blossoms into the full grown strides of the advanced mathematics for astrophysics!_

























