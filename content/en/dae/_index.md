---
title: "dae"
weight: 30
description: "Planned, wave 3: an IDA-type solver for differential-algebraic equations."
---

<!-- From go-scikit/roadmap, bib/systems-units-formats-visualization.md, sections 1a, 2b, 3a, 4 and 5, and PLAN.md. Change it there first. -->

**Status: planned (wave 3). No code exists.** The package name is provisional,
and so is the home: the bibliography leaves open whether the solver lives here
or in go-numerics/integrate, which has stiff ODE solvers (Radau, BDF) and event
handling but no DAE support and no mass matrix.

## What it will provide

- Index-1 systems in fully implicit form, F(t, y, y') = 0, by a variable-order,
  variable-step BDF method (DASSL and IDA).
- Semi-explicit systems M y' = f and mass-matrix problems, through Radau IIA.
- Consistent initial conditions.
- Events: zero crossings and discontinuities, restarting on dense output.

Without an expression system, only index-1 systems and user-supplied reduced
systems are feasible; index reduction belongs to `model`.

## References

| Subject | Reference |
| --- | --- |
| DAE, BDF | Brenan, Campbell and Petzold, *Numerical Solution of Initial-Value Problems in Differential-Algebraic Equations*, SIAM 1996, [doi:10.1137/1.9781611971224](https://doi.org/10.1137/1.9781611971224); Petzold, SIAM J. Sci. Stat. Comput. 4(1), 1983, [doi:10.1137/0904010](https://doi.org/10.1137/0904010) |
| Radau, mass matrix | Hairer and Wanner, *Solving Ordinary Differential Equations II*, 2nd ed., Springer 1996, [doi:10.1007/978-3-642-05221-7](https://doi.org/10.1007/978-3-642-05221-7) |
| consistent initial conditions | Brown, Hindmarsh and Petzold, SIAM J. Sci. Comput. 19(5), 1998, [doi:10.1137/S1064827595289996](https://doi.org/10.1137/S1064827595289996) |

## How it will be validated

| Area | Criterion |
| --- | --- |
| DAE | error against the reference solution of the Bari test set at a stated tolerance; index-1 constraint residual; final-time error, constraint drift, steps, Newton iterations; event times to 1e-10 |

Reference implementations: [SUNDIALS](https://github.com/LLNL/sundials) (IDA,
BSD-3-Clause), DASSL from netlib (SLATEC, public domain) and Hairer's RADAU5
(BSD-2-style licence). The Bari
[Test Set for IVP Solvers](https://archimede.uniba.it/~testset/testsetivpsolvers/)
is the corpus; its licence is unspecified, so the cases are generated and cited,
never redistributed. Every item also needs unit tests at 100% coverage and a
performance table against the reference.
