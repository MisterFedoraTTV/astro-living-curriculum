# Stage 10 — Astrophysics Integration (Stars, Galaxies & Observation)
*(Raspberry Pi 3 Edition — Extended Plan)*

## Overview
This final stage unifies all prior knowledge into applied astrophysics.  
You’ll model stellar evolution, analyze spectra, and simulate galactic and orbital dynamics — all from your Raspberry Pi.

By the end of this stage, you’ll:
- Use thermodynamics and nuclear fusion to model stellar interiors.  
- Simulate galactic orbits using Newtonian and relativistic corrections.  
- Analyze astronomical data (spectra, images, or time series).  
- Design an independent capstone research project.

---

## Lesson 1 — Stellar Physics & Energy Generation

### 🎯 Objectives
- Model the structure and evolution of stars.  
- Understand hydrostatic equilibrium and nuclear fusion.  
- Compute temperature, pressure, and luminosity relations.

### 🧩 Concept Focus
Hydrostatic balance · Ideal gas law · Fusion and luminosity  

### 🧪 Example — Hydrostatic Equilibrium Model
```python
import numpy as np, matplotlib.pyplot as plt

R = np.linspace(0,1,100)
rho_c = 150e3  # kg/m³
P_c = 1e16     # Pa
P = P_c * (1 - R**2)
rho = rho_c * (1 - R**2)
plt.plot(R,P,label='Pressure')
plt.plot(R,rho,label='Density')
plt.xlabel('Normalized Radius'); plt.legend()
plt.title('Simplified Stellar Interior Model'); plt.show()

💬 Reflection

    What happens if pressure falls faster than density?

    Why does fusion only occur in the core?

Lesson 2 — Blackbody Radiation & Stellar Spectra
🎯 Objectives

    Model stellar spectra using Planck’s law.

    Compute luminosity and color indices.

    Classify stars on an H–R diagram.

🧩 Concept Focus

Planck radiation · Wien’s law · Luminosity–temperature relationship
🧪 Example — Spectral Comparison

import numpy as np, matplotlib.pyplot as plt

h, c, k = 6.626e-34, 3e8, 1.381e-23
def planck(lam, T):
    return (2*h*c**2 / lam**5) / (np.exp(h*c/(lam*k*T)) - 1)

lam = np.linspace(1e-7, 3e-6, 400)
for T in [3000, 5800, 10000]:
    plt.plot(lam*1e9, planck(lam, T), label=f'{T} K')
plt.xlabel('Wavelength (nm)'); plt.ylabel('Intensity (arb.)')
plt.title('Blackbody Spectra of Stars'); plt.legend(); plt.grid(); plt.show()

💬 Reflection

    Why do hotter stars peak at shorter wavelengths?

    How does this relate to star color and temperature?

Lesson 3 — Galactic Structure & Dark Matter
🎯 Objectives

    Simulate rotation curves of spiral galaxies.

    Compare observed and theoretical velocity profiles.

    Infer dark matter effects.

🧩 Concept Focus

Mass distribution · Centripetal force · Dark matter halos
🧪 Example — Galaxy Rotation Curve

import numpy as np, matplotlib.pyplot as plt

G = 6.674e-11
r = np.linspace(0.1, 30, 200) * 3.086e19  # 0.1–30 kpc
M_visible = 1e41 * (1 - np.exp(-r/(5*3.086e19)))  # luminous mass
v_visible = np.sqrt(G*M_visible/r)

# Add dark matter halo
rho0, r0 = 1e-21, 5*3.086e19
M_dark = 4*np.pi*rho0*r0**3*(np.log((r+r0)/r0) - r/(r+r0))
v_total = np.sqrt(G*(M_visible + M_dark)/r)

plt.plot(r/3.086e19, v_visible/1e3, label='Visible Mass Only')
plt.plot(r/3.086e19, v_total/1e3, label='With Dark Matter')
plt.xlabel('Radius (kpc)'); plt.ylabel('Velocity (km/s)')
plt.title('Galaxy Rotation Curve'); plt.legend(); plt.show()

💬 Reflection

    Why does visible mass alone fail to explain observed rotation?

    What role does dark matter play in galactic stability?

Lesson 4 — Observation, Data, and Light Curves
🎯 Objectives

    Analyze photometric or spectral data.

    Generate and interpret a light curve.

    Identify periodic or transient phenomena.

🧩 Concept Focus

Flux · Magnitude · Periodic signals
🧪 Example — Simulated Exoplanet Transit

import numpy as np, matplotlib.pyplot as plt

time = np.linspace(0,10,500)
flux = np.ones_like(time)
flux[(time>4) & (time<6)] -= 0.02  # small dip during transit
plt.plot(time, flux)
plt.xlabel('Time (days)'); plt.ylabel('Normalized Flux')
plt.title('Simulated Exoplanet Transit Light Curve')
plt.show()

💬 Reflection

    How would you detect planets or variable stars from light curves?

    What sources of noise must be considered in real observations?

Lesson 5 — Capstone Project: Stellar Evolution or Galactic Simulation
🎯 Objectives

    Integrate physics, math, and code into a full astrophysics simulation.

    Choose between stellar, galactic, or orbital modeling.

    Document, visualize, and publish results on GitHub.

🧩 Example Project Options

Option 1 – Stellar Evolution Model
Simulate star lifetime based on mass and luminosity:

import numpy as np
M = np.linspace(0.1, 50, 100)  # solar masses
L = M**3.5
lifetime = 1e10 / L  # years
import matplotlib.pyplot as plt
plt.loglog(M, lifetime)
plt.xlabel('Mass (M☉)'); plt.ylabel('Lifetime (years)')
plt.title('Main-Sequence Stellar Lifetime')
plt.grid(); plt.show()

Option 2 – Galaxy Merger Visualization
Use two gravitational potentials to model galaxy interaction (optional REBOUND add-on).
💬 Deliverables

    Jupyter notebook report with equations, code, and discussion.

    Visual outputs (plots, animations).

    README summary of findings.

💻 Git Workflow Recap

git add projects/capstone_project.ipynb
git commit -m "Stage 10 capstone: astrophysics integration project"
git push

📈 Checkpoint

Completed a working simulation or data analysis project

Connected theory to physical observables

Published final notebook and documentation on GitHub
