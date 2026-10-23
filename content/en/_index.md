---
title: "go-control documentation"
linkTitle: "Home"
type: docs
cascade:
  type: docs
description: "Control systems and DAE solvers in pure Go (CGO=0). Planned, wave 3 of the go-scikit roadmap: no library exists yet."
---

**go-control is planned.** It is the organisation the
[go-scikit parity plan](https://github.com/go-scikit/roadmap/blob/main/PLAN.md)
names for what MATLAB's Control System Toolbox, Simulink's solvers,
Mathematica's control systems and Maple's MapleSim offer. No library exists, no
code is written and nothing is released: these pages say what the organisation
will cover, in which wave, and what each part will be validated against.

## Scope

LTI models and their algebra, time and frequency responses, stability margins,
Riccati and Lyapunov equations, LQR and LQG, pole placement, discretisation, a
solver for differential-algebraic equations, and, last, MapleSim-style symbolic
acausal modelling. System identification and robust control are in the
bibliography but not scheduled by the plan.

## Plan

| Item in the plan | What | Wave |
| --- | --- | --- |
| 12 | LTI models, frequency and time responses, Riccati and Lyapunov, LQR and LQG, `c2d` | 3 |
| 22 | `model`: symbolic acausal modelling, after the DAE solver and go-symbolic | 4 |

The plan is [PLAN.md](https://github.com/go-scikit/roadmap/blob/main/PLAN.md);
where each item stands is [STATUS.md](https://github.com/go-scikit/roadmap/blob/main/STATUS.md).
The facts behind the scope, the references and the validation measures are in
the roadmap's
[bibliography](https://github.com/go-scikit/roadmap/blob/main/bib/systems-units-formats-visualization.md).
Control needs dense linear algebra that go-ndarray's `linalg` does not have yet:
real Schur form with eigenvalue reordering, QZ and `expm`.

## The planned packages

The names are provisional.

| Package | Status | What it will provide |
| --- | --- | --- |
| [lti]({{< relref "lti" >}}) | planned (wave 3) | models, algebra, poles and zeros, responses, margins |
| [design]({{< relref "design" >}}) | planned (wave 3) | Riccati, Lyapunov, LQR, LQG, pole placement, `c2d` |
| [dae]({{< relref "dae" >}}) | planned (wave 3) | an IDA-type DAE solver |
| [model]({{< relref "model" >}}) | planned (wave 4) | symbolic acausal modelling |

## Status

Nothing is released, so there is nothing to install. When a package is released
its page becomes the package's own documentation, and this site's version label
follows the newest release, as in the other go-scikit organisations.
