# Emergence Beyond the Bare Rules: Stability-Modulated Dissipation, Selective Attraction in Stochastic Node Dynamics

A toy simulation in Java investigating whether minimal local rules (Brownian perturbation, stability-dependent energy leakage, selective attraction toward stabilizing neighbors, and utility-driven edge formation and pruning) can yield emergent mesoscale structures that are richer and harder to summarize than the bare equations suggest on the surface.

This project is built as an evolving, long-horizon research codebase with adaptive metrics and progressive system complexity. Every experiment is designed either to surface an emergent regime worth reporting or to sharpen the instruments used to detect one.

---

## Research Thesis & The Emergence Bet

On paper, the local rules are intentionally plain: a node wanders under Brownian noise, leaks energy at a rate tied to its internal stability, pulls gently toward compatible or stabilizing neighbors, and forms or sheds links under local budget pressure. Yet coupled nonlinear systems often cross thresholds where simple local primitives produce unexpected global organization, such as filaments, branching channels, metastable clusters, rhythmic oscillations, or abrupt phase shifts.

This repository is structured around pursuing that breakthrough honestly without assuming it is even possible to begin with in this scope and framing.

---

## Core Mechanics

### 1. Node & Interaction Domain
- **Node State & Relations:** Nodes carry internal state (such as energy, stability, or local attributes) and optional spatial coordinates or neighbor relations depending on the active experiment. Where spatial or temporal dimensions are used, interactions may be bounded by proximity, reach, internal stability and arbitrary properties that abstractly represent a gradient from positive to negative.
- **Flexible Structure:** Rather than locking every run into a fixed spatial-temporal network assumption, interaction rules can stay abstract or incorporate space and time only where they serve the search for emergent structures.

### 2. Energy, Capacity & Stability-Modulated Decay
- **Energy as Primary Driver:** Energy drives activity, state transitions, attraction, and connection dynamics across the system. These external injections push large amounts of energy into specific regions or nodes, potentially driving a trajectory to maximize stability as unstable structures decay energy at unsustainable rates before being able to form any meaningful structure and are therefore pruned out of the system when they lose all energy.
- **Node Energy Capacity:** Each node has a soft cap around how much energy it can hold, as it may resist applied energy by trying to form connections that dissipate energy efficiently. Energy cannot float around as a substate, it is only an internal dial of each node. Energy can also be directly transferred between two nodes of close proximity.
- **Internal Stability:** An arbitrary bounded metric on each node whose primary role is governing how fast its energy decays.  
- **Stability-Modulated Decay:** Every entity incurs a baseline decay rate per tick scaled by its internal stability.

### 3. Stochastic Diffusion & Selective Attraction
- **Stochastic Perturbation:** A seeded `SplittableRandom` stream drives reproducible random motion or state jitter each step, continuously moving nodes around across time.
- **Selective Attraction:** Nodes experience graded pull toward other nodes whose properties (opposite energy gradients, or compatible state) help move them toward stability. This creates a direct tension between random exploration and selective cohesion.

### 4. Connection Formation, Pruning & Dormancy
- **Cluster Formation:** A node can combine with any number of nodes to hopefully form structures.
