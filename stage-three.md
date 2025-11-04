# Stage 3 — Linear Algebra (Vectors, Matrices & Transformations)
*(Raspberry Pi 3 Edition — Extended Plan)*  

## Overview  
Linear Algebra describes how systems interact: vectors represent directions and magnitudes, while matrices describe how those vectors transform, rotate, or scale.  
In physics, these tools model everything from forces and rotations to quantum states and gravitational fields.

---

## Lesson 1 — Vectors in 2D and 3D

### 🎯 Objectives  
- Represent and manipulate vectors numerically.  
- Compute magnitude, direction, and dot product.  
- Visualize vectors in 2D and 3D plots.  

### 🧩 Concept Focus  
Vectors · Components · Inner product  

### 🧰 Tools  
`numpy`, `matplotlib` (with `Axes3D`)  

### 🧪 Example — Basic Vector Operations  
```python
import numpy as np
v1 = np.array([3, 4])
v2 = np.array([1, -2])
dot = np.dot(v1, v2)
magnitude = np.linalg.norm(v1)
angle = np.arccos(dot / (np.linalg.norm(v1)*np.linalg.norm(v2)))
print(f"|v1|={magnitude:.2f}, dot={dot}, angle={np.degrees(angle):.1f}°")

🧪 3D Visualization

import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.quiver(0,0,0,2,1,3,length=1,normalize=True)
ax.set_xlim(0,2); ax.set_ylim(0,2); ax.set_zlim(0,3)
ax.set_title("3D Vector Example")
plt.show()

💬 Checkpoint

Can compute vector operations in Python

    Understands geometric meaning of dot product

Lesson 2 — Matrices & Transformations
🎯 Objectives

    Define a matrix as a linear transformation.

    Perform addition, multiplication, and transposition.

    Apply transformations to geometric vectors.

🧩 Concept Focus

Matrix operations · Linear mapping · Rotation matrices
🧪 Example — 2D Rotation

import numpy as np, matplotlib.pyplot as plt

theta = np.deg2rad(45)
R = np.array([[np.cos(theta), -np.sin(theta)],
              [np.sin(theta),  np.cos(theta)]])
v = np.array([1,0])
v_rot = R @ v

plt.quiver(0,0,v[0],v[1],angles='xy',scale_units='xy',scale=1,label='Original')
plt.quiver(0,0,v_rot[0],v_rot[1],angles='xy',scale_units='xy',scale=1,label='Rotated')
plt.legend(); plt.axis('equal'); plt.grid(); plt.show()

💬 Checkpoint

Multiplies matrices and vectors correctly

    Understands transformation matrices visually

Lesson 3 — Systems of Equations & Matrix Inverses
🎯 Objectives

    Solve simultaneous linear equations using matrix methods.

    Understand determinants and inverses.

🧩 Concept Focus

Matrix inversion · Determinant · Ax = b
🧪 Example — Solving Equations

import numpy as np
A = np.array([[2,1], [1,3]])
b = np.array([8,13])
x = np.linalg.solve(A,b)
print("Solution:", x)

💬 Reflection

    What does a zero determinant mean?

    How does singularity relate to dependent equations?

💬 Checkpoint

Solves systems using np.linalg.solve()

    Computes determinant and understands meaning

Lesson 4 — Eigenvalues & Eigenvectors
🎯 Objectives

    Compute eigenvalues and eigenvectors of a matrix.

    Understand stability and principal directions.

🧩 Concept Focus

Eigen decomposition · Principal components · Physical stability
🧪 Example — Eigenvalues in Action

import numpy as np
A = np.array([[2,1],[1,2]])
vals, vecs = np.linalg.eig(A)
print("Eigenvalues:", vals)
print("Eigenvectors:\n", vecs)

💬 Reflection

    How do eigenvalues relate to stability or resonance?

    Why do certain directions remain unchanged under transformation?

💬 Checkpoint

Computes eigenvalues/eigenvectors

    Interprets them geometrically

Lesson 5 — Mini Project: Orbital Plane Transformation
🎯 Objectives

    Apply vector and matrix concepts to 3D orbital motion.

    Rotate orbital data into a new reference plane.

🧪 Project Code — Orbital Rotation

import numpy as np
from mpl_toolkits.mplot3d import Axes3D
import matplotlib.pyplot as plt

# Define simple circular orbit in XY plane
theta = np.linspace(0,2*np.pi,100)
x = np.cos(theta)
y = np.sin(theta)
z = np.zeros_like(theta)

# Rotation about X-axis by 30°
angle = np.deg2rad(30)
R = np.array([[1,0,0],
              [0,np.cos(angle),-np.sin(angle)],
              [0,np.sin(angle), np.cos(angle)]])
coords = np.vstack((x,y,z))
rotated = R @ coords

fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.plot(rotated[0],rotated[1],rotated[2])
ax.set_title('Orbit Rotated by 30° about X-axis')
plt.show()

💬 Reflection

    What does the rotation physically represent?

    How do matrix transformations describe orbital inclination?

💻 Git Workflow Recap

git add projects/orbital_plane_rotation.ipynb
git commit -m "Stage 3 project: orbital rotation simulation"
git push

📈 Checkpoint

Visualizes orbit in 3D

Understands how matrix operations describe rotations

Commits final notebook to GitHub
