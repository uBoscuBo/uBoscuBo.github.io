<!-- Code Example -->

---
layout: project
title: "GNN for Molecular Property Prediction"
description: >-
  A graph neural network framework for predicting thermodynamic and kinetic
  properties of organic molecules, achieving DFT-level accuracy at 1000× lower
  computational cost.
tags: [Python, PyTorch, Graph Neural Networks, Chemistry, DFT]
date: 2024-01-15
github: "https://github.com/yourusername/gnn-mol-props"
demo: ""
paper: ""
image: ""
featured: true
status: "completed"
published: false
---

## Overview

Traditional quantum chemistry methods like Density Functional Theory (DFT) are
highly accurate but computationally prohibitive for large-scale molecular screening.
This project trains a graph neural network on a dataset of 130,000 molecules to
predict formation energies, HOMO-LUMO gaps, and reaction barriers.

## Motivation

High-throughput virtual screening of catalysts and drug candidates requires
fast, accurate property prediction. Surrogate ML models can bridge the gap
between speed and accuracy.

## Technical Approach

The model represents each molecule as a graph where:
- **Nodes** encode atomic features (element, charge, hybridization)
- **Edges** encode bond features (type, length, angle)
- **Message passing** aggregates local chemical environment over 4 layers

```python
class MoleculeGNN(nn.Module):
    def __init__(self, node_dim=64, edge_dim=32, depth=4):
        super().__init__()
        self.convs = nn.ModuleList([
            GATConv(node_dim, node_dim, edge_dim=edge_dim)
            for _ in range(depth)
        ])
        self.readout = nn.Linear(node_dim, 1)
```

## Results

| Property       | MAE (our model) | MAE (baseline) |
|----------------|-----------------|----------------|
| Formation energy | 0.042 eV      | 0.18 eV        |
| HOMO-LUMO gap   | 0.11 eV        | 0.34 eV        |
| Reaction barrier| 0.09 eV        | 0.27 eV        |

Inference is **1,200× faster** than single-point DFT on identical hardware.

## Key Challenges

- **Data curation**: Filtering QM9 and PCQM4Mv2 datasets for consistency  
- **Transfer learning**: Pre-training on PubChem and fine-tuning on small datasets  
- **Uncertainty quantification**: Ensemble predictions for out-of-distribution molecules

## Future Work

- Extend to transition metal complexes (catalysis applications)
- Active learning loop for intelligent data acquisition
- Integration with Aspen Plus for process-level optimization
