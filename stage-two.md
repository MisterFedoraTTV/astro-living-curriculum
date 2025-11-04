 Stage 2 — Calculus I (Differential & Integral Basics)
*(Raspberry Pi 3 Edition — Extended Plan)*  

## Overview  
This stage bridges algebra and physics: you’ll learn how to describe **change** — how quantities grow, shrink, or move over time.  
You’ll use both analytic methods (formulas) and computational ones (Python plots, symbolic algebra, and numerical integration).

---

## Lesson 1 — The Concept of a Derivative

### 🎯 Objectives  
- Understand a derivative as a *rate of change*.  
- Compute simple derivatives symbolically and numerically.  
- Plot slopes using Python.  

### 🧩 Concept Focus  
Limits · Difference quotient · Slope interpretation  

### 🧰 Tools  
`sympy`, `numpy`, `matplotlib`  

### 💻 CLI Setup  
Ensure environment is active:  
```bash
cd ~/astro_lab
source ~/astro_env/bin/activate
jupyter lab

🧪 Example — Analytical and Numerical Derivative

import sympy as sp, numpy as np, matplotlib.pyplot as plt
x = sp.symbols('x')
f = x**2
df = sp.diff(f, x)
print("Derivative:", df)

# Numeric check
x_vals = np.linspace(-5,5,200)
y_vals = x_vals**2
dy = np.gradient(y_vals, x_vals)
plt.plot(x_vals, y_vals, label='f(x)')
plt.plot(x_vals, dy, label="df/dx (numerical)")
plt.legend(); plt.grid(); plt.show()

💬 Checkpoint

Understands derivative as slope

Computes derivative using SymPy

    Visualizes function and derivative curves

Lesson 2 — Motion, Velocity, and Acceleration
🎯 Objectives

    Connect derivatives to physical quantities: position, velocity, and acceleration.

    Derive motion equations from calculus principles.

    Visualize dynamic change.

🧩 Concept Focus

Kinematics · Derivative chain · Real-world interpretation
🧪 Example — Free-Fall Simulation

import numpy as np, matplotlib.pyplot as plt
t = np.linspace(0, 5, 100)
x = 0.5 * 9.81 * t**2
v = np.gradient(x, t)
a = np.gradient(v, t)
plt.plot(t,x,label='Position (m)')
plt.plot(t,v,label='Velocity (m/s)')
plt.plot(t,a,label='Acceleration (m/s²)')
plt.legend(); plt.xlabel('Time (s)'); plt.title('Free-Fall Dynamics'); plt.show()

💬 Reflection

    How do the curves relate?

    What does constant acceleration look like?

    What happens if g changes?

Lesson 3 — The Concept of an Integral
🎯 Objectives

    Understand the integral as area under a curve.

    Compute symbolic and numeric integrals.

    Interpret area as accumulated change.

🧩 Concept Focus

Definite integral · Antiderivative · Accumulation
🧪 Example — Displacement from Velocity

import sympy as sp
t = sp.symbols('t')
v = 3*t**2
x = sp.integrate(v, t)
print("Integral of v(t):", x, "+ C")

🧪 Numeric Integration (Trapezoidal Rule)

import numpy as np
t = np.linspace(0,5,100)
v = 3*t**2
x = np.trapz(v, t)
print(f"Displacement over 5 s: {x:.2f} m")

💬 Checkpoint

Computes integrals in SymPy and NumPy

    Relates integral to physical area

Lesson 4 — Fundamental Theorem of Calculus
🎯 Objectives

    Relate differentiation and integration as inverse operations.

    Verify the theorem computationally.

🧩 Concept Focus

Derivatives undo integrals · Continuous motion consistency
🧪 Example — Consistency Check

import sympy as sp
x = sp.symbols('x')
f = sp.sin(x)
F = sp.integrate(f, x)
dF = sp.diff(F, x)
print("f(x):", f)
print("Integral F(x):", F)
print("Derivative of F:", dF)

💬 Reflection

    Why do integration and differentiation “undo” each other?

    What does this mean for predicting future motion from data?

Lesson 5 — Mini Project: Launch to the Stars
🎯 Objectives

    Apply calculus to simulate the motion of a rocket.

    Combine differentiation and integration to model velocity and position over time.

    Visualize results.

🧪 Project Code

import numpy as np, matplotlib.pyplot as plt

# Rocket thrust model (simple)
t = np.linspace(0,50,500)
a = 9*np.exp(-t/10) - 9.81   # decreasing thrust minus gravity
v = np.cumsum(a) * (t[1]-t[0])  # integrate acceleration
x = np.cumsum(v) * (t[1]-t[0])  # integrate velocity

plt.figure(figsize=(8,5))
plt.plot(t,a,label='Acceleration')
plt.plot(t,v,label='Velocity')
plt.plot(t,x,label='Altitude')
plt.xlabel('Time (s)'); plt.legend(); plt.grid()
plt.title('Rocket Launch Simulation')
plt.show()

💬 Reflection

    What happens if thrust decay is slower?

    At what time does velocity reach zero (apogee)?

    How does calculus allow us to predict this behavior?

💻 Git Workflow Recap

git add projects/rocket_launch.ipynb
git commit -m "Stage 2 project: Rocket launch simulation"
git push

📈 Checkpoint

Understands differentiation & integration conceptually

Can simulate motion from first principles

Submits project notebook to GitHub





