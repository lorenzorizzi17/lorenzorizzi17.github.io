---
layout: page
title: Numerical Methods for Soft Matter
description: Advanced Monte Carlo and Molecular Dynamics simulations (Ising, Active Matter, Langevin).
img: assets/img/soft_matter/preview.jpg # <--- Scegli una thumb quadrata
importance: 1
category: work
related_publications: false
---

This project encompasses the comprehensive codebase and analysis developed for the **Numerical Methods for Soft Matter** course at the University of Padova (2025/2026). The work focuses on the implementation of stochastic algorithms, Monte Carlo (MC) methods, and Molecular Dynamics (MD) engines to study equilibrium and non-equilibrium statistical physics. Here, I will only display a selected subset of the assigned homeworks! 

The full theoretical background and detailed results are available in the attached reports.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        <a href="/assets/pdf/Report_Part1.pdf" class="btn btn-sm z-depth-0" role="button" target="_blank">Download Report Part 1 (PDF)</a>
        <a href="/assets/pdf/Report_Part2.pdf" class="btn btn-sm z-depth-0" role="button" target="_blank">Download Report Part 2 (PDF)</a>
    </div>
</div>

---

## Part 1: Monte Carlo & Lattice Models

The first part of the project is all about Monte Carlo techniques, from the problem of random variables generation to the simulation of lattice systems, with a strong focus on phase transitions and criticality.


### The 2D Ising Model
Are you really a statistical physicist if you've never implemented the beloved Ising spin model? 

And in fact, a core component of this work is the simulation of the 2D Ising model at zero field using the **Metropolis algorithm** with local dynamics.
I performed a deep analysis of the phase transition, studying order parameters such as the magnetization ($m$), the energy ($E$), specific Heat ($C_v$), and susceptibility ($\chi$).

Critical dynamics were analyzed by estimating the **Correlation Length** ($\xi$), verifying Critical Slowing Down, and computing the Integrated Correlation Time.

> **Note:** The efficiency-critical code (C++) is hosted in the external [YAIS Repository](https://github.com/tuouser/yais), featuring varying MCMC engines.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img src="/assets/img/soft_matter/500_1.png" class="img-fluid rounded z-depth-1" alt="Ising Magnetization">
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <img src="/assets/img/soft_matter/500_4.png" class="img-fluid rounded z-depth-1" alt="Ising Susceptibility">
    </div>
</div>
<div class="caption">
    Left: Magnetization density vs Temperature showing the phase transition. Right: Divergence of magnetic susceptibility near $T_c$.
</div>



### 3. Active Ising Model (NESS)
We extended the analysis to Non-Equilibrium Steady States (NESS) by simulating the **Active Ising Model** in 2D. We characterized the system's rich phase diagram in the $(\rho, T)$ plane, identifying Gas, Liquid, and Coexistence phases typical of active matter systems.

---

## Part 2: Molecular Dynamics & Stochastic Processes

The second part focuses on continuum systems, time evolution, and advanced sampling techniques.

### 1. Molecular Dynamics (MD) Engines
We implemented efficient MD simulations for **(Patchy) Hard Spheres** utilizing **Cell Lists** and **Verlet Lists** to optimize neighbor searching from $\mathcal{O}(N^2)$ to $\mathcal{O}(N)$.
The integration was performed using symplectic integrators like **Velocity Verlet**, contrasting them with 1st order Euler methods.

### 2. Thermostats & Ensembles
To simulate the Canonical Ensemble ($NVT$), we implemented and compared different algorithmic thermostats:
* **Berendsen Thermostat:** Weak coupling to a heat bath.
* **Andersen Thermostat:** Stochastic collision simulation.

### 3. Advanced Sampling: Parallel Tempering
To overcome energy barriers and extract thermal averages at arbitrary inverse temperatures $\beta$, we implemented **Multiple Markov Chains** with **Parallel Tempering** (Replica Exchange) and the **Multiple Histograms** (WHAM) method.

### 4. Stochastic Dynamics
Finally, we explored continuous-time Markov processes using the **Gillespie Algorithm** and numerical implementations of **Langevin** and **Brownian** dynamics.