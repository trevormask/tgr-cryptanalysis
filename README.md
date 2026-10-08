# Terminal Geometric Resonance (TGR) Cryptanalysis

This repository contains the complete cryptanalytic dismantling of the Terminal Geometric Resonance (TGR) framework, a proposed side-channel countermeasure for elliptic curve scalar multiplication on secp256k1. 

The research proves that the TGR state space collapses to a 1-dimensional rational manifold, providing zero cryptographic depth or side-channel resistance. All theoretical claims are accompanied by reproducible Python implementations.

## 🔑 Key Findings

1. **1-Dimensional Rational Manifold:** All TGR intermediate variables ($M, T, J, C, \Phi, u$) are trivially invertible rational functions of the Master Coordinate $u$ and public coordinates.
2. **Public Geometry Template Factorization:** Every direct-branch variable is a linear projection $\mathcal{V}_k = d \cdot \tau_k(1)$, where $\tau_k(1)$ is a purely public geometric tag. This yields $H(d \mid \mathcal{V}_k, P) = 0$.
3. **Canonical Integer-Offset Leakage:** The TGR intermediate $A_d = (d - Y) \bmod p$ satisfies $A_d = (p - Y) + d$ over the integers $\mathbb{Z}$ (for $d < Y$). This exposes the secret scalar as a raw, unreduced integer offset from the public anchor $p - Y$.
4. **Secret-Isolating Cancellation:** Cross-power operations on the hierarchy (e.g., $M^2 / T$) perfectly cancel the public geometric tags, isolating the secret scalar $d$ in $\mathcal{O}(1)$ operations without requiring explicit knowledge of the base projection $R_{\text{norm}}$.
5. **Dynamic Lattice Vulnerability:** The state evolution forms a public affine dynamical system, creating a bidiagonal matrix structure highly susceptible to Hidden Number Problem (HNP) lattice reduction attacks.

## 🚀 Reproduction Instructions

All empirical validations can be reproduced locally using Python 3.

### Prerequisites
```bash
pip install numpy scipy
