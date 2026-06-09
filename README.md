# Physics-Informed Neural Network for Inverse Stokes Flow

## Overview

This repository documents a Physics-Informed Neural Network (PINN) framework developed for solving inverse problems governed by the incompressible Stokes equations.

The framework combines sparse observational data with governing physical laws to reconstruct flow quantities such as slip velocity $u_s$ at the active particle surfaces that is hard to measure experimentally, while enforcing consistency with the underlying fluid dynamics.

The methodology is applicable to a variety of low-Reynolds-number flow problems, including microfluidics, soft matter systems, active matter, and interfacial hydrodynamics.

---

## Governing Equations

The model is based on the incompressible Stokes equations

$$
-\nabla p + \mu \nabla^2 \boldsymbol{u} = \boldsymbol{0}
$$

$$
\nabla \cdot \boldsymbol{u} = 0
$$

where

* $\boldsymbol{u}$ denotes the velocity field,
* $p$ denotes the pressure field,
* $\mu$ is the dynamic viscosity.

### Boundary Conditions

Fluid velocity on the active particle surface

$$\boldsymbol{u}|_{S} = \boldsymbol{U} + \boldsymbol{\Omega} \times (\boldsymbol{r}-\boldsymbol{r}_0) + \boldsymbol{u}_s$$

where $\boldsymbol{U}$ and $\boldsymbol{\Omega}$ are the translational and rotational velocities of the active particle and $\boldsymbol{u}_s$ is the slip velocity at the particle surface.

In case there is a solid boundaries present, the fluid velocity follows no slip conditions on the boundaries:

$$\boldsymbol{u}_{wall} = 0$$

---

## PINN Formulation

A neural network is trained to approximate the unknown solution fields.

The loss function combines:

* Data mismatch loss
* PDE residual loss
* Boundary condition loss

$$\mathcal{L} = \mathcal{L}_{Phys} + \lambda_{data} \mathcal{L}_{data}$$

where

$$\mathcal{L}_{Phys} = \mathcal{L}_{PDE} + \mathcal{L}_{BC} + \mathcal{L}_{wall}$$

Automatic differentiation is used to evaluate the derivatives appearing in the governing equations.

---

## Methodology

The workflow consists of:

1. Data preparation and normalization
2. Physics-informed neural network construction
3. Automatic differentiation of PDE residuals
4. Optimization of the composite loss function
5. Reconstruction of velocity and pressure fields
6. Predicting the velocity at the active particle surface
7. Validation against reference solutions

---

## Representative Results

### Network Architecture

<img src="architecture.jpg" alt="Architecture Diagram" width="50"/>

### Training Algorithm

![Workflow](figures/Algorithm.jpg)

### Loss Function Components

![Loss Function](figures/loss_function.png)

### Predicted Velocity Field

![Velocity Prediction](figures/velocity_prediction.png)

### Predicted Pressure Field

![Pressure Prediction](figures/pressure_prediction.png)

### Convergence History

![Convergence](figures/convergence_history.png)

---

## Publication

The scientific results associated with this work are available in:

https://arxiv.org/abs/2511.22723

---

## Code Availability

The implementation is not publicly distributed. This repository documents the methodology, architecture, and representative results of the PINN framework.

---

## Research Areas

* Physics-Informed Neural Networks (PINNs)
* Scientific Machine Learning
* Inverse Problems
* Stokes Flow
* Computational Fluid Dynamics
* Soft Matter Physics
* Active Matter
* Scientific Computing
