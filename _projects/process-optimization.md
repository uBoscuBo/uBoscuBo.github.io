<!-- Code Example -->

---
layout: project
title: "ML-Accelerated Process Optimization"
description: >-
  Surrogate-model-driven optimization of a chemical distillation train using
  Bayesian optimization, reducing energy consumption by 18% while maintaining
  product purity constraints.
tags: [Python, Bayesian Optimization, Aspen Plus, Process Engineering, MATLAB]
date: 2023-08-01
github: "https://github.com/yourusername/process-opt"
demo: ""
paper: ""
image: ""
featured: true
status: "completed"
published: false
---

## Overview

Chemical process optimization traditionally requires many expensive simulations
(e.g., Aspen Plus) to evaluate each candidate operating point. This project
replaces the simulator with a Gaussian Process surrogate and applies Bayesian
optimization to find energy-optimal conditions in a fraction of the time.

## Problem Statement

A 3-column distillation train separating a ternary mixture has:
- 14 decision variables (reflux ratios, feed stages, pressures)
- 4 product purity constraints (≥99.5% per spec)
- Objective: minimize reboiler duty (proxy for energy cost)

## Approach

### 1. Data Collection
Latin Hypercube Sampling (LHS) of 500 initial simulation runs via the Aspen Plus
COM API, yielding a labeled dataset of `(operating conditions → energy, purity)`.

### 2. Surrogate Model
A multi-output Gaussian Process fitted separately for each output:

```python
from sklearn.gaussian_process import GaussianProcessRegressor
from sklearn.gaussian_process.kernels import Matern

gp = GaussianProcessRegressor(
    kernel=Matern(nu=2.5),
    n_restarts_optimizer=10,
    normalize_y=True
)
gp.fit(X_train, y_energy)
```

### 3. Bayesian Optimization
Expected Improvement (EI) acquisition function with constraint handling
via probability of feasibility:

```
EI_constrained(x) = EI(x) * ∏ P(g_i(x) ≤ 0)
```

## Results

| Metric              | Baseline | Optimized |
|---------------------|----------|-----------|
| Reboiler duty       | 14.2 MW  | 11.6 MW   |
| Optimization cycles | ~2,000   | 87        |
| Wall-clock time     | ~40 hrs  | 2.5 hrs   |

**18% energy reduction** with 96% fewer simulator calls.

## Tools

- **Aspen Plus** (COM API via Python `win32com`)
- **GPyTorch** for scalable GP regression
- **BoTorch** for acquisition function optimization
- **Plotly** for interactive Pareto front visualization

## dhfdsfsd

dfsfds