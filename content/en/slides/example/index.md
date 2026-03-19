---
title: "Formation of the Solar System"
subtitle: "Theoretical Foundations"
summary: "An introduction to using Hugo Blox Builder's Slides feature."
authors: []
tags: []
categories: []
date: '2026-03-19'
slides:
  theme: black
  highlight_style: dracula
---

## Authors
Arbatova Varvara Petrovna, Karpova Yesenia Alekseevna, Dagdelen Zeynap Rejepovna, Byugdanyuk Anna Vasilievna, Lyupp Sofya Romanovna

Peoples' Friendship University of Russia (RUDN)

Moscow, Ordzhonikidze St. 3

---

# Introduction

The formation of planetary systems is a key process in the evolution of the Universe

The theory explains the origin of the Solar System and exoplanets

**Objective:** To study the theoretical foundations of the formation of a planetary system from a gas and dust cloud

---

# Origin of the Universe

![The Big Bang ~13.7 billion years ago](image/1.png)

Expansion and cooling → particles → atoms → galaxies → stars

---

# Schmidt's Theory (1944)

![Formation of a protoplanetary disk](image/2.png)

1) A rotating gas and dust cloud contracts
2) Rotation speed increases (law of conservation of angular momentum)
3) The cloud flattens into a disk
4) Rings form on the periphery → condense into planets

---

# Laws of Motion

**Kepler's Third Law:**

$$v \sim \frac{1}{\sqrt{r}}$$

Velocity decreases with distance from the center

Used to set initial velocities of particles

---

# Gravitational Interaction

**Potential Energy:**

$$U_i = -\sum_{j \neq i} \frac{\gamma m_i m_j}{r_{ij}}$$

Gravity is a long-range force

Requires accounting for all particle pairs

Complexity O(N²) limits the model size

---

# Repulsion and Friction Forces

![Schematic representation](image/3.png)

Upon approach $b < R_i + R_j$:

**Repulsion:** $F^r(b) = k\left(\left(\frac{a}{b}\right)^8 - 1\right)$

**Friction:** $F_f = \beta W_{\perp} F^r(b) \mathbf{n}$

Friction is perpendicular to the radius vector, directed against the motion

---

# Particle Rotation

Moment of inertia: $I = \frac{2}{5} m R^2$

Equation of rotation: $I\varepsilon = R\sum\frac{b}{R_i+R_j}F^f$

Rotational energy: $E_{\text{rot}} = \frac{I\omega^2}{2}$

---

# Particle Coalescence

Upon complete coalescence:

$m = m_i + m_j$

$R = \sqrt[3]{R_i^3 + R_j^3}$

$\mathbf{r} = \frac{m_i\mathbf{r}_i + m_j\mathbf{r}_j}{m_i + m_j}$

$\mathbf{v} = \frac{m_i\mathbf{v}_i + m_j\mathbf{v}_j}{m_i + m_j}$

Conserves the mass and momentum of the system

---

# Key Mechanisms

| Mechanism | Role |
|-----------|------|
| Gravity | Attraction of particles, formation of clumps |
| Repulsion | Prevents particles from passing through each other |
| Friction | Energy dissipation, conversion to heat |
| Rotation | Accounting for angular velocity during collisions |
| Coalescence | Growth of planets from small particles |

---

# Conclusion

The theoretical foundations of the formation of the Solar System have been reviewed:

- Cosmological prehistory (Big Bang, supernovae)
- Schmidt's theory of protoplanetary disk formation
- Physical mechanisms: gravity, repulsion, friction, rotation, coalescence

The obtained foundations will be used for numerical modeling