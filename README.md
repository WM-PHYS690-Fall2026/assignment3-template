# Assignment 3: Particle Charge Deposition and a Poisson Field Solver

This is the starter repository for PHYS690 Assignment 3. You will build a small electrostatic field-solver workflow inspired by particle-in-cell (PIC) plasma codes: deposit prescribed charged particles onto a grid, solve Poisson's equation for the electrostatic potential, compute the electric field, and study how numerical choices change the result.

The assignment connects the validation workflow from Lecture 10, the finite-difference boundary-value-problem methods from Lecture 11, and the particle-to-grid field-solver pipeline from Lecture 12:

- [Course lecture repository](https://github.com/jrstevenjlab/gradcompphys/tree/main/lectures)
- [Lecture 10: Initial-value ODEs](https://github.com/jrstevenjlab/gradcompphys/blob/main/lectures/lecture10_9_29_26_ivp_ode.ipynb)
- [Lecture 11: Boundary-value problems and PDEs](https://github.com/jrstevenjlab/gradcompphys/blob/main/lectures/lecture11_10_6_26_bvp_pde.ipynb)
- [Lecture 12: Source-to-field applications](https://github.com/jrstevenjlab/gradcompphys/blob/main/lectures/lecture12_10_15_26.ipynb)

The particle set is prescribed inside the notebook and script, so no external data files are required. This keeps the assignment reproducible while still connecting directly to the particle-to-grid and field-solver steps used in production PIC codes.

## Repository Layout

```text
.
├── .gitignore
├── README.md
├── requirements.txt
├── figures/
│   └── .gitkeep
├── notebooks/
│   └── assignment3_pic_poisson_solver.ipynb
└── scripts/
    └── make_pic_poisson_comparison.py
```

## Setup

Open this repository folder in VS Code and use `Terminal > New Terminal`.

On macOS:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

On Windows Git Bash:

```bash
python -m venv .venv
source .venv/Scripts/activate
python -m pip install -r requirements.txt
```

After installing packages, open `notebooks/assignment3_pic_poisson_solver.ipynb` and select the `.venv` Python kernel.

## Assignment Work

Complete the guided notebook in `notebooks/`. You will:

- inspect a prescribed, reproducible set of charged macroparticles;
- deposit particle charge onto a 2D grid with both NGP and CIC;
- assemble and solve a finite-difference Poisson equation with grounded Dirichlet boundaries;
- validate the Poisson solver against a smooth manufactured solution;
- compute `E_x` and `E_y` from the potential;
- test Gauss's law as a diagnostic of the full source-to-field pipeline;
- compare how the field changes with both grid spacing and charge-assignment scheme;
- explain how this controlled calculation connects to the charge-deposition and field-solve steps of PIC plasma simulations.

You must also complete the command-line script:

```bash
python scripts/make_pic_poisson_comparison.py
```

The completed script should reproduce and save the final comparison figures, such as:

- `figures/pic_poisson_potential_field.png`
- `figures/pic_poisson_manufactured_convergence.png`
- `figures/pic_poisson_grid_or_scheme_comparison.png`
- `figures/pic_poisson_summary.csv`

Update this `README.md` so another person can rerun your notebook and script from a fresh clone.

## References

- WarpX theory overview: https://warpx.readthedocs.io/en/latest/theory/intro.html
- Smilei PIC code documentation: https://smileipic.github.io/Smilei/
- Z. Donko et al., *eduPIC: an introductory particle based code for radio-frequency plasma simulation*, arXiv: https://arxiv.org/abs/2103.09642
- Course lectures: https://github.com/jrstevenjlab/gradcompphys/tree/main/lectures
- Lecture 10 IVP and numerical-validation notebook: https://github.com/jrstevenjlab/gradcompphys/blob/main/lectures/lecture10_9_29_26_ivp_ode.ipynb
- Lecture 11 finite-difference Poisson/BVP notebook: https://github.com/jrstevenjlab/gradcompphys/blob/main/lectures/lecture11_10_6_26_bvp_pde.ipynb
- Lecture 12 source-to-field and particle-deposition notebook: https://github.com/jrstevenjlab/gradcompphys/blob/main/lectures/lecture12_10_15_26.ipynb

## Submission

This repository should remain private inside the `WM-PHYS690-Fall2026` GitHub organization. Make meaningful commits as you work, then push your final work.

Finally, submit a pull request from the `submission` branch into `main` in your private assignment repository. This will inform Prof. Stevens that your submission is ready to be evaluated.
