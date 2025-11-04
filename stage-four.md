 Stage 4 — Classical Mechanics (Newtonian Physics & Energy Systems)
*(Raspberry Pi 3 Edition — Extended Plan)*  

## Overview  
This stage brings together math, programming, and physics to explore **Newton’s laws of motion**, **forces**, **energy**, and **momentum**.  
By the end, you’ll simulate dynamic systems and understand the quantitative relationship between force and motion.

---

## Lesson 1 — Newton’s Laws of Motion  

### 🎯 Objectives  
- Learn and apply Newton’s three laws.  
- Connect force, mass, and acceleration computationally.  
- Simulate motion from simple force functions.  

### 🧩 Concept Focus  
Force as vector · Inertia · F = ma  

### 🧪 Example — Constant Force  
```python
import numpy as np, matplotlib.pyplot as plt

m = 1.0      # kg
F = 2.0      # N
t = np.linspace(0, 10, 100)
a = F/m
v = a*t
x = 0.5*a*t**2

plt.plot(t,x,label='Displacement')
plt.plot(t,v,label='Velocity')
plt.xlabel('Time (s)'); plt.legend(); plt.grid()
plt.title("Constant Force Motion (F = ma)")
plt.show()

💬 Reflection

    How do the velocity and position curves relate?

    How does doubling mass affect motion?

💬 Checkpoint

Understands how F = ma governs motion

    Produces correct acceleration plots

Lesson 2 — Forces in One and Two Dimensions
🎯 Objectives

    Compute net forces from multiple components.

    Visualize motion in 2D under constant and varying forces.

🧩 Concept Focus

Vector decomposition · Gravitational acceleration · Friction and tension
🧪 Example — 2D Force Decomposition

import numpy as np
theta = np.deg2rad(30)
W = 9.81    # N
Wx = W*np.sin(theta)
Wy = W*np.cos(theta)
print(f"Components: Wx={Wx:.2f} N, Wy={Wy:.2f} N")

🧪 Visualization — Inclined Plane

import matplotlib.pyplot as plt
plt.quiver(0,0,Wx,0,angles='xy',scale_units='xy',scale=1,label='Parallel')
plt.quiver(0,0,0,Wy,angles='xy',scale_units='xy',scale=1,label='Perpendicular')
plt.legend(); plt.axis('equal'); plt.title('Force Components on an Incline')
plt.show()

💬 Checkpoint

Resolves vector forces into components

    Visualizes results in 2D plots

Lesson 3 — Work, Energy, and Power
🎯 Objectives

    Derive relationships among work, kinetic energy, and potential energy.

    Use Python to integrate force functions over displacement.

🧩 Concept Focus

Work-energy theorem · Potential wells · Power and rate of change
🧪 Example — Work Done by Variable Force

import numpy as np
from scipy.integrate import quad

def F(x): return 3*x**2
W, _ = quad(F, 0, 2)
print(f"Work from x=0→2 = {W:.2f} J")

🧪 Visualization — Energy Conversion

x = np.linspace(0,10,100)
U = 0.5*9.81*x
K = 50 - U
plt.plot(x,U,label='Potential Energy')
plt.plot(x,K,label='Kinetic Energy')
plt.legend(); plt.xlabel('Position (m)')
plt.ylabel('Energy (J)'); plt.title('Energy Conversion'); plt.show()

💬 Reflection

    When is total energy conserved?

    What happens if you include friction (energy loss)?

Lesson 4 — Momentum and Collisions
🎯 Objectives

    Define linear momentum and impulse.

    Model collisions and verify conservation laws.

🧩 Concept Focus

Momentum conservation · Elastic vs inelastic collisions
🧪 Example — Elastic Collision

m1, m2 = 2.0, 1.0
u1, u2 = 3.0, -1.0
v1 = ((m1 - m2)/(m1 + m2))*u1 + (2*m2/(m1 + m2))*u2
v2 = (2*m1/(m1 + m2))*u1 + ((m2 - m1)/(m1 + m2))*u2
print(f"Final velocities: v1={v1:.2f} m/s, v2={v2:.2f} m/s")

🧪 Visualization — Momentum Tracking

import matplotlib.pyplot as plt
masses = [m1, m2]
u = np.array([u1, u2])
v = np.array([v1, v2])
plt.bar(['Before','After'], [sum(masses*u), sum(masses*v)])
plt.ylabel('Total Momentum (kg·m/s)')
plt.title('Momentum Conservation')
plt.show()

💬 Reflection

    What changes in inelastic collisions?

    How does energy differ from momentum conservation?

Lesson 5 — Mini Project: Planetary Gravity Simulation
🎯 Objectives

    Apply Newton’s law of universal gravitation.

    Simulate orbital motion numerically.

    Visualize gravitational trajectories.

🧩 Concept Focus

Inverse-square law · Differential motion · Numerical integration
🧪 Project Code — Two-Body Simulation

import numpy as np, matplotlib.pyplot as plt

G = 6.674e-11
M = 1.989e30  # Sun
m = 5.972e24  # Earth
dt = 60*60*6  # 6-hour steps
steps = 1500

r = np.zeros((steps,2))
v = np.zeros((steps,2))
r[0] = [1.496e11, 0]
v[0] = [0, 29780]

for i in range(steps-1):
    rmag = np.linalg.norm(r[i])
    a = -G*M*r[i]/rmag**3
    v[i+1] = v[i] + a*dt
    r[i+1] = r[i] + v[i+1]*dt

plt.plot(r[:,0], r[:,1])
plt.scatter(0,0,color='orange',label='Sun')
plt.axis('equal'); plt.legend(); plt.title('Earth Orbit Simulation')
plt.xlabel('x (m)'); plt.ylabel('y (m)')
plt.show()

💬 Reflection

    What happens if time step dt is too large?

    How would you extend this to 3D or multiple bodies?

💻 Git Workflow Recap

git add projects/gravity_orbit_sim.ipynb
git commit -m "Stage 4 project: planetary gravity simulation"
git push

📈 Checkpoint

Understands forces, energy, and motion integration

Runs orbit simulation successfully

Explains energy/momentum conservation qualitatively
