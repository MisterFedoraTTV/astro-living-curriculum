# Stage 5 — Electromagnetism (Fields, Potentials & Waves)
*(Raspberry Pi 3 Edition — Extended Plan)*

## Overview
Electromagnetism describes how electric charges and magnetic fields interact.  
By the end of this stage you’ll:
- Compute electric fields and potentials from charge distributions.  
- Visualize magnetic fields from moving charges.  
- Simulate charged-particle motion in combined E and B fields.  
- Understand how light emerges as an electromagnetic wave.

---

## Lesson 1 — Electric Charge & Coulomb’s Law

### 🎯 Objectives
- Model point charges and compute electric forces.  
- Visualize vector fields in 2-D space.  
- Relate field lines to potential.

### 🧩 Concept Focus
Coulomb’s Law · Superposition · Field vectors  

### 🧪 Example — Electric Field from Two Charges
```python
import numpy as np, matplotlib.pyplot as plt

k = 8.99e9
q1, q2 = 1e-6, -1e-6
r1, r2 = np.array([-0.05,0]), np.array([0.05,0])
x, y = np.meshgrid(np.linspace(-0.1,0.1,40), np.linspace(-0.1,0.1,40))
Ex, Ey = np.zeros_like(x), np.zeros_like(y)

for (q, r) in [(q1, r1), (q2, r2)]:
    rx, ry = x - r[0], y - r[1]
    rmag = np.sqrt(rx**2 + ry**2)
    Ex += k*q*rx/rmag**3
    Ey += k*q*ry/rmag**3

plt.streamplot(x, y, Ex, Ey, color=np.log(np.hypot(Ex,Ey)))
plt.scatter([-0.05,0.05],[0,0],c=['r','b'],s=60)
plt.axis('equal'); plt.title('Electric Field of Dipole')
plt.show()

💬 Checkpoint

Plots electric field vectors correctly

    Explains why field lines flow from + to – charges

Lesson 2 — Electric Potential and Energy
🎯 Objectives

    Derive electric potential V from E.

    Compute potential energy between charges.

    Plot equipotential lines.

🧩 Concept Focus

Gradient · Potential difference · Work in electric fields
🧪 Example — Potential Mapping

import numpy as np, matplotlib.pyplot as plt

k, q = 8.99e9, 1e-6
x, y = np.meshgrid(np.linspace(-0.1,0.1,100), np.linspace(-0.1,0.1,100))
r = np.sqrt(x**2 + y**2)
V = k*q / r
plt.contourf(x,y,V,levels=50)
plt.colorbar(label='Potential (V)')
plt.axis('equal'); plt.title('Equipotential Lines')
plt.show()

💬 Reflection

    How are equipotential lines oriented relative to E-field lines?

    Why is potential energy a scalar while E is a vector?

Lesson 3 — Magnetism and Moving Charges
🎯 Objectives

    Understand magnetic fields from currents.

    Compute Lorentz force q(v × B).

    Visualize circular motion of charges in B-fields.

🧩 Concept Focus

Lorentz force · Right-hand rule · Cyclotron motion
🧪 Example — Charged Particle in Magnetic Field

import numpy as np, matplotlib.pyplot as plt

q, m, Bz = 1.6e-19, 9.1e-31, 1e-3
v = np.array([1e6,0,0])
r = np.array([0,0,0])
dt = 1e-9; steps = 1000
trajectory = []

for _ in range(steps):
    F = q * np.cross(v, [0,0,Bz])
    a = F/m
    v += a*dt
    r += v*dt
    trajectory.append(r.copy())

traj = np.array(trajectory)
plt.plot(traj[:,0], traj[:,1])
plt.axis('equal'); plt.title('Circular Motion in Magnetic Field')
plt.xlabel('x (m)'); plt.ylabel('y (m)')
plt.show()

💬 Checkpoint

Particle moves in circle with constant speed

    Understands force perpendicular to velocity

Lesson 4 — Electromagnetic Induction & Waves
🎯 Objectives

    Explore Faraday’s law and changing flux.

    Simulate a simple AC generator and wave propagation.

🧩 Concept Focus

Induction · Flux · Sinusoidal fields
🧪 Example — Induced Voltage

import numpy as np, matplotlib.pyplot as plt
B0, A, f = 0.01, 0.1, 60
t = np.linspace(0, 0.05, 1000)
Phi = B0*A*np.cos(2*np.pi*f*t)
emf = -np.gradient(Phi, t)
plt.plot(t, emf); plt.xlabel('Time (s)'); plt.ylabel('EMF (V)')
plt.title('Induced EMF in Rotating Loop'); plt.show()

🧪 Wave Visualization

x = np.linspace(0,10,200)
t = 0
E = np.sin(2*np.pi*(x - t))
B = np.sin(2*np.pi*(x - t))
plt.plot(x,E,label='E-field')
plt.plot(x,B,label='B-field')
plt.legend(); plt.xlabel('Position'); plt.title('Electromagnetic Wave Snapshot'); plt.show()

💬 Checkpoint

Understands flux changes induce EMF

    Identifies E and B fields in phase and perpendicular

Lesson 5 — Mini Project: Charged Particle in Crossed E and B Fields
🎯 Objectives

    Simulate motion in combined electric and magnetic fields.

    Demonstrate the conditions for uniform velocity and cycloid paths.

🧩 Concept Focus

Lorentz force superposition · Numerical integration
🧪 Project Code

import numpy as np, matplotlib.pyplot as plt

q, m = 1.6e-19, 9.1e-31
E = np.array([0, 1e3, 0])
B = np.array([0, 0, 1e-3])
v = np.array([1e6, 0, 0])
r = np.zeros(3)
dt = 1e-9; steps = 2000
traj = []

for _ in range(steps):
    F = q*(E + np.cross(v, B))
    a = F/m
    v += a*dt
    r += v*dt
    traj.append(r.copy())

traj = np.array(traj)
plt.plot(traj[:,0], traj[:,1])
plt.axis('equal'); plt.xlabel('x'); plt.ylabel('y')
plt.title('Charged Particle in Crossed E and B Fields')
plt.show()

💬 Reflection

    How does field strength affect trajectory shape?

    What ratio of E/B creates uniform motion (no deflection)?

💻 Git Workflow Recap

git add projects/crossed_fields.ipynb
git commit -m "Stage 5 project: charged particle in E and B fields"
git push

📈 Checkpoint

Simulates field-driven motion successfully

Explains Lorentz force qualitatively

Commits project to GitHub
