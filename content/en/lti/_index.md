---
title: "lti"
weight: 10
description: "Planned, wave 3: linear time-invariant models, their algebra, responses and margins."
---

<!-- From go-scikit/roadmap, bib/systems-units-formats-visualization.md, sections 1a, 2a, 3a and 4, and PLAN.md item 12. Change it there first. -->

**Status: planned (wave 3). No code exists.** The package name is provisional.

## What it will provide

- Model types: transfer function, zero-pole-gain, state space and frequency-response
  data.
- Model algebra: series, parallel and feedback connections.
- Poles, zeros, DC gain and minimal realisation.
- Time response (step, impulse, arbitrary input, initial condition), exact for
  LTI models through the matrix exponential.
- Frequency response, Nyquist encirclements, root locus and stability margins.

It needs the non-symmetric eigenvalue solver, QZ and `expm` that go-ndarray's
`linalg` does not yet provide.

## References

| Subject | Reference |
| --- | --- |
| frequency response | Laub, "Efficient multivariable frequency response computations", IEEE TAC 26(2), 1981, [doi:10.1109/TAC.1981.1102602](https://doi.org/10.1109/TAC.1981.1102602): Hessenberg reduction, then one solve per frequency |
| matrix exponential | Al-Mohy and Higham, SIAM J. Matrix Anal. Appl. 31(3), 2009, [doi:10.1137/09074721X](https://doi.org/10.1137/09074721X) |
| stability margins | Skogestad and Postlethwaite, *Multivariable Feedback Control*, 2nd ed., Wiley 2005 |
| textbook examples | Franklin, Powell and Emami-Naeini, *Feedback Control of Dynamic Systems*, 8th ed., Pearson 2019 |

## How it will be validated

| Area | Criterion |
| --- | --- |
| poles and zeros | relative error against the reference after sorting, with the conditioning accounted for |
| frequency response | complex relative error per point against python-control, reported in ULPs of the response |
| `expm` | relative error against a high-precision reference, norm-wise |
| time response | agreement with the `expm`-based exact solution; an ODE-based path is judged with a tolerance |

Reference implementations: [python-control](https://github.com/python-control/python-control)
(BSD-3-Clause; the API template), SciPy's `scipy.signal`, and Octave's `control`
package as an oracle only, since it is GPL. Every item also needs unit tests at
100% coverage and a performance table against the reference, no slower than it
on one core.
