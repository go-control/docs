---
title: "design"
weight: 20
description: "Planned, wave 3: Riccati and Lyapunov equations, LQR and LQG, pole placement and discretisation."
---

<!-- From go-scikit/roadmap, bib/systems-units-formats-visualization.md, sections 1a, 2a, 3a and 4, and PLAN.md item 12. Change it there first. -->

**Status: planned (wave 3). No code exists.** The package name is provisional.

## What it will provide

- Continuous and discrete algebraic Riccati equations (CARE, DARE).
- Lyapunov and Sylvester equations.
- LQR, LQG and Kalman gains.
- Pole placement for multi-input systems.
- Discretisation (`c2d`): zero-order hold, first-order hold, Tustin and matched.

It depends on `lti` and on Schur reordering, QZ and `expm` in go-ndarray's
`linalg`.

## References

| Subject | Reference |
| --- | --- |
| CARE and DARE | Laub, "A Schur method for solving algebraic Riccati equations", IEEE TAC 24(6), 1979, doi:10.1109/TAC.1979.1102178 |
| Riccati refinement | Kleinman, IEEE TAC 13(1), 1968, doi:10.1109/TAC.1968.1098829 |
| Sylvester and Lyapunov | Bartels and Stewart, CACM 15(9), 1972, doi:10.1145/361573.361582; Hammarling, IMA J. Numer. Anal. 2(3), 1982, doi:10.1093/imanum/2.3.303 |
| exact zero-order hold | Van Loan, IEEE TAC 23(3), 1978, doi:10.1109/TAC.1978.1101743 |
| pole placement | Kautsky, Nichols and Van Dooren, Int. J. Control 41(5), 1985, doi:10.1080/0020718508961188 |

## How it will be validated

| Area | Criterion |
| --- | --- |
| Riccati and Lyapunov | relative residual below 1e3·n·eps, a solution symmetric to one ulp, closed-loop poles in the left half-plane; the worst residual over the benchmark set and the median ratio against SLICOT and SciPy are reported |
| `c2d` | relative error against a high-precision reference, 10·eps norm-wise |

Reference implementations: [SLICOT-Reference](https://github.com/SLICOT/SLICOT-Reference)
(BSD-3-Clause in the repository; each routine's header is to be checked, and the
commit recorded, before any port), SciPy (`solve_continuous_are`, `place_poles`),
python-control and Octave's `control` package as oracles. The SLICOT benchmark
collections and COMPleib are the corpora. Every item also needs unit tests at
100% coverage and a performance table against the reference.
