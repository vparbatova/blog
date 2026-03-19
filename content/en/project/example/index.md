---
summary: First stage of the project
tags:
  - Deep Learning
date: '2016-04-27T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  caption: Photo by rawpixel on Unsplash
  focal_point: Smart

links:
  - icon: twitter
    icon_pack: fab
    name: Follow
    url: https://twitter.com/georgecushen
url_code: ''
url_pdf: ''
url_slides: ''
url_video: ''

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: example

author:
  - name: Arbatova Varvara Petrovna
    degrees: BSc
    orcid: 0000-0002-0877-7063
    email: 1132236020@rudn.ru
    affiliation:
      name: Peoples' Friendship University of Russia
      country: Russian Federation
      postal-code: 117198
      city: Moscow
      address: 3 Ordzhonikidze St.
  - name: Karpova Esenia Alekseevna
    degrees: BSc
    email: 1132236008@rudn.ru
    affiliation:
      name: Peoples' Friendship University of Russia
      country: Russian Federation
      postal-code: 117198
      city: Moscow
      address: 3 Ordzhonikidze St.
  - name: Dagdelen Zeynep Rejepovna
    degrees: BSc
    email: 1132236052@rudn.ru
    affiliation:
      name: Peoples' Friendship University of Russia
      country: Russian Federation
      postal-code: 117198
      city: Moscow
      address: 3 Ordzhonikidze St.
  - name: Bogdanyuk Anna Vasilievna
    degrees: BSc
    email: 1132236023@rudn.ru
    affiliation:
      name: Peoples' Friendship University of Russia
      country: Russian Federation
      postal-code: 117198
      city: Moscow
      address: 3 Ordzhonikidze St.
  - name: Lyupp Sofya Romanovna
    degrees: BSc
    email: 1132236039@rudn.ru
    affiliation:
      name: Peoples' Friendship University of Russia
      country: Russian Federation
      postal-code: 117198
      city: Moscow
      address: 3 Ordzhonikidze St.
title: "Project Work. Formation of a Planetary System"
subtitle: "First Stage"
license: "CC BY"
---

# Objective

The objective of this work is the numerical simulation of the formation of a planetary system from a gas and dust cloud using methods of molecular dynamics, gravitational interaction, friction forces, and particle coalescence.

# Tasks

1.  Write a program simulating the motion of N points in a plane, experiencing attraction to a fixed central point, not interacting with each other, and moving in orbits with the first cosmic velocity.

2.  Introduce gravitational interaction between particles. Remove the fixed central point. Add repulsion between particles when they approach a distance less than the sum of their radii. Display the kinetic and potential energies on the screen. Make the total momentum of the system zero. Add friction forces between particles.

3.  Include in the model the angular velocities of rotation around their own axis for each particle.

4.  Simulate the three-dimensional case of N interacting particles with repulsion but without friction. Display the projections of particle motion on the XY, YZ, XZ planes. Plot the dependence of kinetic, potential, and total energy on time.

5.  Introduce particle coalescence in the three-dimensional case after they approach within a small distance. When a larger particle forms, the total mass and momentum of the system must be conserved.

6.  Introduce friction forces. Explain the behavior of kinetic and potential energy.

7.  Introduce particles of two types with different masses and corresponding radii. Add friction between particles. Display a graph of the energy converted into heat. Explain the total energy graph. Introduce particles with randomly assigned masses and corresponding radii.

# Formation of a Planetary System

## Introduction

The formation of planetary systems is one of the key processes in the evolution of the Universe. According to modern understanding, stars and their planetary systems form as a result of the gravitational collapse of interstellar gas and dust clouds. During collapse, the cloud fragments, forming protostars and protoplanetary disks, within which planets subsequently form.

## Theoretical Description of the Problem

### Origin of Stars and Stellar Systems

According to the theory of Friedman, Lemaître, and Gamow, the Universe originated from a point as a result of the Big Bang approximately 13.7 billion years ago ([Fig. @fig-001]).

![Big Bang](image/1.png){#fig-001 width=70%}

At this moment, taken as the starting point, the Universe had a very small size and extremely high density and temperature. Since then, the Universe has been continuously expanding and cooling. During expansion and cooling, elementary particles formed, then atoms, and under the influence of gravitational instability, the first structures began to take shape: protoclusters, protogalaxies, galaxies, and finally, stars.

Stars tens of times more massive than the Sun evolve rapidly and explode as supernovae, ejecting heavy elements from which new stars and planets later form.

### Formation of the Solar System

According to the theory of the Solar System's formation proposed by Otto Schmidt (USSR, 1944), the gas and dust cloud from which the Sun and planets later formed was rotating. As the cloud contracted gravitationally, the distance of all its parts from the rotation axis decreased, and the rotation speed of the contracting cloud increased. In the plane perpendicular to the rotation axis, contraction occurred more slowly, so the initially spherical cloud became increasingly flattened. Due to gravitational instability at the periphery of the forming disk, a ring of matter separated. The remaining cloud continued to contract and rotate even faster. Then another ring of matter separated, and the rings condensed into planets ([Fig. @fig-002]).

![Theory of Solar System formation](image/2.png){#fig-002 width=70%} 

The dependence of planetary orbital velocity on distance from the Sun follows Kepler's third law - velocity decreases inversely proportional to the square root of the distance from the center:

$$
v \sim \frac{1}{\sqrt{r}}
$$

where $r$ is the distance from the center.

## Mathematical Model

### Gravitational Interaction

We will simulate one of the stages of the Universe's evolution — the formation of a certain "solar" system from interstellar gas. Since the number of simulated particles is quite limited, we can say that in this model, planets form from already formed gas-dust clumps, which are represented by the specified particles.

The potential energy of the gravitational interaction of a particle system is described by the formula:

$$
U_i = -\sum_{j \neq i} \frac{\gamma m_i m_j}{r_{ij}}, \quad U = \frac{1}{2} \sum_i U_i
$$

where $\gamma$ is the gravitational constant, $m_i$, $m_j$ are the particle masses, and $r_{ij}$ is the distance between them.

The total potential energy of the particle system is:

$$
U = \frac{1}{2} \sum_{i} U_{i} 
$$

The factor $\frac{1}{2}$ is necessary because the interaction energy between each pair of particles is counted twice in this sum.

Gravity is a long-range force, requiring consideration of interactions between all pairs of particles. Therefore, interactions between distant particles cannot be ignored. This leads to $O(N^2)$ complexity, limiting the size of simulatable systems, even on modern computers.

### Initial Conditions

The initial distribution of particles in the plane is set randomly; with a sufficiently large number of particles, the distribution within the disk plane will be uniform if, for the two-dimensional case, the radius-vector modulus is chosen as $r = r_0*\sqrt{\text{random}}$:

-   Radius: $r = r_0 \cdot \sqrt{\text{random}}$
-   Angle: $\alpha = 2\pi \cdot \text{random}$
-   Initial velocity, found according to Kepler's third law:

$$
v_x = -y \cdot \omega_0 \left( \frac{r_0}{r} \right)^{3/2}, \quad v_y = x \cdot \omega_0 \left( \frac{r_0}{r} \right)^{3/2}, \quad v_z = 0
$$

where $\omega_0$ is the angular velocity at distance $r_0$, and $r_0$ is the radius of the gas-dust disk.

### Repulsion and Friction Forces

For particles whose center-to-center distance is less than the sum of their radii, it is necessary to introduce friction and repulsion forces ([Fig. @fig-003]).

![Friction and repulsion forces](image/3.png){#fig-003 width=70%}

This is done for programming convenience, as in reality, the collision of two gas-dust clouds would lead to their coalescence, and at very high velocities, they might fragment into smaller ones.

#### The repulsion force can be taken as:

$$
F^r(b) = k \left( \left( \frac{a}{b} \right)^8 - 1 \right)
$$

where $a = R_i + R_j$ is the sum of the radii of particles $i$ and $j$,
and $b = |\mathbf{r}_{i,j}| = |\mathbf{r}_i - \mathbf{r}_j|$ is the magnitude of the interaction radius-vector.

#### Friction Force

The friction force is perpendicular to the interaction radius-vector **b** and is directed against the relative motion of the particles. The unit vector along the friction force for the two-dimensional model is:

$$
n = \frac{(-b_y, b_x)}{\sqrt{b_x^2 + b_y^2}}
$$

The relative velocity of the particle surfaces, perpendicular to the radius:

$$
W_\perp = (v_i - v_j) \cdot n - \omega_i R_i - \omega_j R_j
$$

where $\omega_i$ and $\omega_j$ are the angular rotational velocities of particles $i$ and $j$, and $W = \mathbf{v}_i - \mathbf{v}_j$ is the relative velocity of the two interacting particles.

In the simplest approximation, the friction coefficient is defined as:

$$
\mu = \beta W_{\perp} 
$$

where:
- $\beta$ is a constant coefficient,
- $W_{\perp}$ is the perpendicular component of the relative velocity $W$.

The magnitude of the friction force is:

$$
F^f = \mu F^r(b), \quad \mu = \beta W_\perp
$$

where:
- $\mu$ is the friction coefficient, dependent on the velocity $W_{\perp}$,
- $F_{r}(b)$ is the radial interaction force, dependent on the distance $b$.

And then the friction force vector is:

$$
\mathbf{F}_f = \beta W_\perp F^r(b) \mathbf{n}
$$

### Particle Rotation

The angular velocity of each particle can be found using the system of equations:

$$
I_i \varepsilon_i = R_i \sum \frac{b}{R_i + R_j} F^f_{ij}, \quad \frac{d\omega_i}{dt} = \varepsilon_i
$$

where the moment of inertia is defined as:

$$
I_i = \frac{2}{5} m_i R_i^2
$$

and the rotational energy:

$$
E_{\text{rot}} = \frac{I_i \omega_i^2}{2}
$$

For a system with friction forces, the total energy is not conserved; part of the energy is converted into heat due to friction. The energy converted into heat can be found as the difference between the initial and current total energy.

### Particle Coalescence

Complete coalescence of a particle pair is possible. As a result, one particle forms, whose radius is calculated as:

- $R = \sqrt[3]{R_i^3 + R_j^3}$

The mass equals the sum of the masses of the coalesced clouds:

- $m = m_i + m_j$

and the coordinates of the new particle are calculated by the formula:

- $\mathbf{r} = \frac{m_i \mathbf{r}_i + m_j \mathbf{r}_j}{m_i + m_j}$

The velocity is calculated similarly:

- $\mathbf{v} = \frac{m_i \mathbf{v}_i + m_j \mathbf{v}_j}{m_i + m_j}$

It should be noted that when particles coalesce, the gravitational energy of the resulting particle is not equal to the sum of the gravitational energies of the original particles. Then the gravitational energy of the new particle is:

$$
E_g = -\frac{\gamma m^2}{2R}
$$

## Model Description

### Two-Dimensional Model with Central Attraction

The first stage simulates the motion of particles in a plane under the influence of a fixed central mass. Particles move in orbits with the first cosmic velocity, without interacting with each other.

### Introducing Gravity and Repulsion

The central point is removed, and gravitational interaction between particles is introduced. When particles approach a distance less than the sum of their radii, a repulsion force is activated. The total momentum of the system is monitored (it should be zero). Kinetic and potential energies are displayed on the screen.

### Accounting for Rotation

Angular velocities of particle rotation around their own axes are added. A friction force is introduced.

### Three-Dimensional Model

The simulation is moved into three-dimensional space. Projections of motion onto the XY, XZ, YZ planes are displayed. Graphs of energy dependence on time are plotted.

### Particle Coalescence

A coalescence mechanism is introduced into the three-dimensional model when particles approach each other. Mass and momentum of the system are conserved.

### Friction and Energy Dissipation

Friction forces are introduced. The behavior of kinetic and potential energy is analyzed. Part of the energy is converted into heat.

### Particles of Different Types

Particles of two types with different masses and radii are introduced. Friction is added. A graph of the energy converted into heat is displayed. Subsequently, masses and radii are assigned randomly.

## Conclusion

As a result of this work, the formation of a planetary system was investigated, and the formulas for constructing a numerical model of planetary system formation from a gas and dust cloud were studied. The model includes gravitational interaction, repulsion and friction forces, rotation, and particle coalescence.

# Conclusions

We conducted research for the numerical simulation of the formation of a planetary system from a gas and dust cloud using methods of molecular dynamics, gravitational interaction, friction forces, and particle coalescence.

# References {.unnumbered}

- [Medvedev D. A. - Modeling of Physical Processes and Phenomena.](https://esystem.rudn.ru/pluginfile.php/3094549/mod_folder/content/0/%D0%9C%D0%B5%D0%B4%D0%B2%D0%B5%D0%B4%D0%B5%D0%B2%20%D0%94.%20%D0%90.%20-%20%D0%9C%D0%BE%D0%B4%D0%B5%D0%BB%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5%20%D1%84%D0%B8%D0%B7%D0%B8%D1%87%D0%B5%D1%81%D0%BA%D0%B8%D1%85%20%D0%BF%D1%80%D0%BE%D1%86%D0%B5%D1%81%D1%81%D0%BE%D0%B2%20%D0%B8%20%D1%8F%D0%B2%D0%BB%D0%B5%D0%BD%D0%B8%D0%B9%20%D0%BD%D0%B0%20%D0%9F%D0%9A.pdf?forcedownload=1)

- [Big Bang](https://pikabu.ru/story/paru_slov_o_bolshom_vzryive_7673576?cid=178197280)

- [Origin of the Solar System](http://chudinov.ru/butusov/5/)

::: {#refs}
:::