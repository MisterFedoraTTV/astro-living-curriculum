# 🌠 Living Curriculum — Integrated Physics & Mathematics Roadmap (Self-Study, Free Resources)

*A GitHub-optimized, mobile-friendly roadmap for learning astrophysics through mathematics and computation using only free tools.*

---

## 📚 Table of Contents
1. [Overview](#-overview)
2. [Repository Structure](#-repository-structure)
3. [Stage Summary](#-stage-summary)
4. [Study Workflow](#-study-workflow)
5. [Raspberry Pi 3 AstroDev Environment Setup Guide](#-raspberry-pi-3-astrodev-environment-setup-guide)
6. [2-Month Study Sprint (Stages 1–3)](#-2-month-study-sprint-stages-1-3)
7. [Next Steps](#-next-steps)

---

## 🌌 Overview
A fully integrated, self-guided roadmap in physics, mathematics, and computation — optimized for **free learning**, **practical integration**, and **Raspberry Pi compatibility**.  
Designed for independent learners preparing for **astrophysics and theoretical physics** without formal tuition.

---

## 🧭 Repository Structure
Below are the suggested folders. You can click each one once created in your GitHub repo.

```
astro-living-curriculum/
│
├── [README.md](README.md)                    # This roadmap
├── [stages/](stages/)                        # Stage folders
│   ├── [stage0_orientation/](stages/stage0_orientation/)
│   ├── [stage1_foundations/](stages/stage1_foundations/)
│   ├── [stage2_calculus1/](stages/stage2_calculus1/)
│   ├── [stage3_linear_algebra/](stages/stage3_linear_algebra/)
│   ├── [stage4_mechanics/](stages/stage4_mechanics/)
│   ├── [stage5_electromagnetism/](stages/stage5_electromagnetism/)
│   ├── [stage6_modern_physics/](stages/stage6_modern_physics/)
│   ├── [stage7_computation/](stages/stage7_computation/)
│   ├── [stage8_thermo_quantum/](stages/stage8_thermo_quantum/)
│   ├── [stage9_cosmology_astrodata/](stages/stage9_cosmology_astrodata/)
│   └── [stage10_research_synthesis/](stages/stage10_research_synthesis/)
│
├── [resources/](resources/)
│   ├── [math_free_texts.md](resources/math_free_texts.md)
│   ├── [physics_free_texts.md](resources/physics_free_texts.md)
│   ├── [software_tools.md](resources/software_tools.md)
│   └── [project_templates/](resources/project_templates/)
│
├── [notebooks/](notebooks/)
│   ├── [mechanics_orbit_integrator.ipynb](notebooks/mechanics_orbit_integrator.ipynb)
│   ├── [em_field_line_visualizer.ipynb](notebooks/em_field_line_visualizer.ipynb)
│   └── [astrodata_lightcurve_analysis.ipynb](notebooks/astrodata_lightcurve_analysis.ipynb)
│
└── LICENSE
```

---

## 📘 Stage Summary
| Stage | Focus | Integration Goal | Key Tools |
|--------|--------|------------------|------------|
| **0** | Orientation & Study Skills | Learning workflow | Markdown, GitHub, Jupyter |
| **1** | Foundations (Arithmetic → Pre-Calc) | Physical intuition via dimensional analysis | Khan Academy, Desmos |
| **2** | Calculus I | Motion, orbits, and change | Calculus + Mechanics linkage |
| **3** | Linear Algebra | Vectors, transformations | 2D/3D motion, EM fields |
| **4** | Mechanics | Dynamics, conservation | Python simulation of motion |
| **5** | Electromagnetism | Field theory foundations | Visualization of field lines |
| **6** | Modern Physics | Relativity, atomic physics | Lorentz transformations, spectra |
| **7** | Computation | Coding, numerical integration | Python, Numpy, Matplotlib |
| **8** | Thermodynamics & Quantum | Statistical, quantum thinking | Schrödinger toy models |
| **9** | Cosmology & Astrophysical Data | Observational + theoretical synthesis | Astropy, FITS, real data |
| **10** | Research & Synthesis | Independent project | Open-source collaboration |

---

## 🔧 Study Workflow
1. Each stage has: *Readings → Notes → Projects → Reflections → Integrations*.
2. Every math concept is paired with a physical phenomenon to model.
3. Use Git + Markdown for note-taking and documentation.
4. Publish results and projects openly (GitHub Pages or Notion).

---

## 💻 Raspberry Pi 3 AstroDev Environment Setup Guide

The Raspberry Pi 3 (especially Model B+) can handle nearly all stages up to advanced computation, provided you optimize for performance. This setup prioritizes lightweight, free, open-source tools.

### 🧩 Recommended Hardware
- **Raspberry Pi 3B or 3B+**
- **64GB+ microSD card** (Class 10 or better)
- **Optional USB external storage** for large data sets
- **Ethernet or Wi-Fi connection** for remote Jupyter access

### 🐍 Python Environment
```bash
sudo apt update && sudo apt upgrade
sudo apt install python3 python3-pip python3-venv
pip install numpy scipy sympy matplotlib pandas astropy jupyterlab
```
Launch Jupyter:
```bash
jupyter lab --no-browser --ip=0.0.0.0
```
Access via another device at `http://<pi_ip_address>:8888`

### ⚙️ Recommended Packages by Stage
| Stage | Key Packages |
|--------|----------------|
| 1–3 | `numpy`, `sympy`, `matplotlib` |
| 4–5 | `scipy`, `matplotlib.animation` |
| 6–8 | `astropy`, `pandas`, `plotly` |
| 9–10 | `astroquery`, `scikit-learn` (light use) |

### ⚡ Performance Tips
- Use **vectorized operations** (`numpy`) instead of loops.
- Keep arrays below ~1e6 elements.
- Run **headless** (no GUI) and access via SSH.
- Use a **swap file** or USB SSD for extra memory.
- Offload heavy computation to **Google Colab** or **GitHub Codespaces**.

---

## 🗓️ 2-Month Study Sprint (Stages 1–3)

### Month 1 — Foundations
**Week 1:** Arithmetic, exponents, units → *dimensional analysis project*  
**Week 2:** Algebra & functions → *constant velocity simulation*  
**Week 3:** Trigonometry → *projectile motion in Python*  
**Week 4:** Limits & derivatives → *velocity from position data*

### Month 2 — Calculus & Linear Algebra
**Week 5:** Integration → *constant acceleration notebook*  
**Week 6:** Vectors & transformations → *animated rotation*  
**Week 7:** Matrix operations → *solve force balance*  
**Week 8:** Review → *2D orbit Euler integrator + reflection notes*

Each week:  
- Add `notes.md` + 1 notebook/script  
- Push commits weekly to GitHub  

---

## 🧭 Next Steps
- [ ] Clone your repo and add this README.  
- [ ] Create empty folders listed above.  
- [ ] Begin with Stage 0 setup → [stages/stage0_orientation/](stages/stage0_orientation/).  
- [ ] Use Issues or Discussions for reflection logs.  
- [ ] Share your repo link publicly for feedback!  

---

🪐 *Created for lifelong learners exploring the universe through math and physics.*
