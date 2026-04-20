# Fokker–Planck Mean First Passage Time Approach

Impact of crowding on diffusive search: a Fokker–Planck and first passage time study of how a spatially varying diffusivity $D(x)$ changes the mean first passage time (MFPT) to a partially absorbing target.

APPM 6470 final project, Spring 2026 — Nirab Hossain, Department of Applied Mathematics, University of Colorado Boulder.

## Summary

We work on the 1D ring $[-\pi,\pi]$ with periodic boundary conditions and a partially absorbing trap of strength $\kappa$ at $x=0$, modelled by a $\delta$-sink in the Fokker–Planck equation. From the backward (adjoint) equation the MFPT reduces to a closed form

$$\langle T\rangle \;=\; \frac{2\pi}{\kappa} \;+\; \frac{1}{\pi}\int_0^\pi \frac{(\pi-y)^2}{D(y)}\,dy,$$

an additive dwell plus travel time. For the piecewise-linear tent profile $D(x)=D_0+D_1(1-|x|/\pi)$ the travel integral has a logarithmic closed form. The analytical result is verified three independent ways:

1. Finite-difference solution of the backward equation (empirical second-order convergence).
2. Crank–Nicolson solution of the forward Fokker–Planck equation, with MFPT recovered from the survival probability.
3. Monte Carlo simulation of the Itô SDE $dx = D'(x)\,dt + \sqrt{2D(x)}\,dW$ with a Poisson trap rule.

All three agree with the analytical formula within their expected error. A final section examines three microscopic stories for $\kappa(D(0))$ and shows that the biologically motivated $\kappa \propto 1/D(0)$ law is the only one producing a non-trivial optimal crowding level.

## Repository layout

```
.
├── final_report.tex        # Master LaTeX document
├── final_report.pdf        # Compiled report
├── sections/               # Report sections + preamble + bibliography
│   ├── preamble.tex
│   ├── 0_abstract.tex ... 9_code.tex
│   └── sample.bib
├── mfpt_code.ipynb         # Jupyter notebook: all numerical experiments
├── files/                  # Figures referenced by the report
└── README.md
```

## Reproducing the results

### Report

Requires a TeX distribution (TeX Live, MiKTeX, or MacTeX). From the repo root:

```bash
pdflatex final_report.tex
bibtex   final_report
pdflatex final_report.tex
pdflatex final_report.tex
```

Or with `latexmk`:

```bash
latexmk -pdf final_report.tex
```

### Numerical experiments

The notebook [`mfpt_code.ipynb`](mfpt_code.ipynb) contains all three numerical methods as stand-alone functions sharing a common spatial discretisation. Reproducing any figure requires re-executing only the corresponding cell.

Dependencies: `numpy`, `scipy`, `matplotlib`. Install with

```bash
pip install numpy scipy matplotlib jupyter
jupyter notebook mfpt_code.ipynb
```

<!-- ## License

Released for academic use. Please cite the report if you build on this work.

## Contact

Nirab Hossain — [nirab@du.ac.bd](mailto:nirab@du.ac.bd) -->
