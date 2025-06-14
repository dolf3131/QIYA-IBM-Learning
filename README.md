# QIYA-IBM-Learning
25-1 Quantum Informatics at Yonsei Academy (QIYA) IBM Learning Project

## QSR-Based Poisson Equation Solver (Sato 2021 Inspired)

This repository implements a hybrid quantum-classical solver for the Poisson equation based on the variational approach proposed in Sato (2021), enhanced via Quantum Sampling Regression (QSR) and surrogate modeling.

## 🔬 Project Motivation

Variational Quantum Algorithms (VQAs), while promising for solving differential equations, suffer from latency and inefficiencies due to repeated quantum-classical optimization loops.  
This project mitigates that by replacing direct quantum evaluations with a **QSR-based surrogate model**, reducing quantum resource usage and allowing multiple eigenvalue extraction more efficiently.

## 🧠 Key Components

- **Ansatz**: `TwoLocal(ry, entanglement='cz')`  
- **Observable**: Hermitian operator derived from discretized Poisson Hamiltonian  
- **Sampling**: Sobol sequence over parameter space  
- **Surrogate Model**: Gaussian Process Regression (GPR)
- **Optimization**: L-BFGS-B over surrogate  
- **Target Problem**: 1D Poisson equation discretized as in Sato (2021)

## 📁 Files

| Filename               | Description |
|------------------------|-------------|
| `QSR_Project.ipynb`    | Full implementation of the VQA-based solver with QSR surrogate modeling |
| `QSR_test.ipynb`       | Unit tests and parameter sweep experiments for verifying the surrogate model and eigenvalue approximation |
| `.gitignore`           | Ignore cache, checkpoints, logs, etc. |

## 📈 Method Overview

1. Generate training samples via Sobol sampling in parameter space
2. Evaluate expectation values ⟨ψ(θ)|H|ψ(θ)⟩ via quantum simulator or actual hardware
3. Train Gaussian Process surrogate model on the dataset
4. Perform classical optimization over the surrogate
5. Optionally repeat with varied initial conditions to capture multiple eigenvalues

## 📚 Reference

- Sato, Y. (2021). *Quantum Variational Solver for the Poisson Equation Using a Minimum Potential Ansatz*.  
  [arXiv:2106.01366](https://arxiv.org/abs/2106.01366)

## 💻 Requirements

- Python ≥ 3.8  
- Qiskit  
- Scikit-learn  
- SciPy  
- matplotlib, pandas (for visualization)

Install with:

```bash
pip install -r requirements.txt
