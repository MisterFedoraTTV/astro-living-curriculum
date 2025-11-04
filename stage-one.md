# Stage 1 — Foundations (Algebra → Pre-Calculus)
*(Raspberry Pi 3 Edition — Extended Plan)*  

## Overview  
This stage introduces the mathematical language of physics: algebra, functions, and trigonometry.  
By the end, you’ll be able to describe motion with equations, visualize data with plots, and connect formulas to physical meaning.

---

## Lesson 1 — Algebra Essentials & Expressions  

### 🎯 Objectives  
- Review arithmetic, exponents, and equation solving.  
- Use algebraic manipulation to isolate variables in physics formulas.  
- Evaluate expressions in Python and verify with hand calculations.  

### 🧩 Concept Focus  
Order of operations · Variables · Linear equations · Scientific notation  

### 💻 CLI Steps  
From your Pi terminal:  
```bash
cd ~/astro_lab
source ~/astro_env/bin/activate
jupyter lab

🧪 Jupyter Example

# Algebra warm-up: solving for time given distance and velocity
d = 150.0   # meters
v = 5.0     # m/s
t = d / v
print(f"Time = {t:.1f} s")

💬 Checkpoint

Understands variable assignment and formula rearrangement

    Can compute physical quantities from simple relations

Lesson 2 — Functions & Graphing with Matplotlib
🎯 Objectives

    Understand functions as input–output mappings.

    Plot linear, quadratic, and exponential functions.

    Explore how parameters change curve shape.

🧩 Concept Focus

Function notation · Parameters · Visualization
🧪 Example

import numpy as np, matplotlib.pyplot as plt
x = np.linspace(-10,10,200)
f1 = 2*x + 3
f2 = x**2
f3 = np.exp(0.2*x)
plt.plot(x,f1,label='linear')
plt.plot(x,f2,label='quadratic')
plt.plot(x,f3,label='exponential')
plt.legend(); plt.xlabel('x'); plt.ylabel('f(x)')
plt.title('Function Families'); plt.grid(); plt.show()

💬 Checkpoint

Knows difference between linear / nonlinear

    Plots multiple functions on one graph

Lesson 3 — Trigonometry & Vectors
🎯 Objectives

    Define sine, cosine, and tangent in terms of right triangles.

    Understand angles in radians.

    Represent 2-D vectors using components and magnitude.

🧩 Concept Focus

Trig functions · Radians · Vector addition
🧪 Example

import numpy as np
theta = np.deg2rad(45)
vx = np.cos(theta); vy = np.sin(theta)
print(f"vx={vx:.3f}, vy={vy:.3f}")

Plot vector arrow:

import matplotlib.pyplot as plt
plt.quiver(0,0,vx,vy,angles='xy',scale_units='xy',scale=1)
plt.xlim(0,1); plt.ylim(0,1)
plt.title('Unit Vector at 45°'); plt.show()

💬 Checkpoint

Understands relationship between degrees / radians

    Can compute vector components and visualize direction

Lesson 4 — Equations of Motion & Units
🎯 Objectives

    Apply algebra and trig to constant-acceleration motion.

    Calculate displacement, velocity, and acceleration numerically.

    Plot motion curves.

🧩 Concept Focus

Kinematic equations · Data arrays · Unit conversion
🧪 Jupyter Example

import numpy as np, matplotlib.pyplot as plt
t = np.linspace(0,5,100)
a = 2.0         # m/s²
v0 = 0.0
x = 0.5*a*t**2 + v0*t
plt.plot(t,x); plt.xlabel('Time (s)'); plt.ylabel('Displacement (m)')
plt.title('Uniform Acceleration'); plt.show()

💬 Checkpoint

Relates graph slope → velocity

    Computes numeric results consistent with SI units

Lesson 5 — Integrating Concepts & Mini Project
🎯 Objectives

    Combine algebra, trig, and functions into a real-world application.

    Document work in Markdown cells.

    Use Git to version your results.

🧪 Mini-Project — Projectile Simulator

Simulate projectile motion neglecting air resistance.

import numpy as np, matplotlib.pyplot as plt
v0 = 20.0       # m/s
theta = np.deg2rad(45)
g = 9.81
t = np.linspace(0, (2*v0*np.sin(theta))/g, 100)
x = v0*np.cos(theta)*t
y = v0*np.sin(theta)*t - 0.5*g*t**2
plt.plot(x,y); plt.xlabel('x (m)'); plt.ylabel('y (m)')
plt.title('Projectile Motion'); plt.axis('equal'); plt.show()

💻 Git Workflow Recap

git add projects/projectile_simulation.ipynb
git commit -m "Stage 1 project: projectile motion"
git push

💬 Reflection Prompts

    How does launch angle affect range?

    What assumptions are made in this model?

    How would you add air resistance?

📈 Checkpoint

Completes and commits notebook

Explains link between equations and plots

    Understands basic trajectory physics

*Congrats on making it through stage one! By now you may have noticed the curriculum works more like a brief overview if you're looking at it per stage, and right now that's exactly what it is. That's an intentional layout until I can figure out exactly what resources I need to add per stage; once that's done this will be a robust and integrated course. For now, just enjoy the samplings here please.*



