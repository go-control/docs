---
title: "model"
weight: 40
description: "Planned, wave 4: MapleSim-style symbolic acausal modelling on top of the DAE solver and go-symbolic."
---

<!-- From go-scikit/roadmap, bib/systems-units-formats-visualization.md, sections 2b and 6, bib/maple.md, and PLAN.md item 22. Change it there first. -->

**Status: planned (wave 4, item 22 of the plan). No code exists.** The package
name is provisional. It comes after the DAE solver and go-symbolic, the size is
XL, and the roadmap states plainly that MapleSim parity is a product, not a
library: MapleSim's component libraries are proprietary and are not planned.

## What it will provide

- Connectors and equation assembly.
- Index reduction by Pantelides' algorithm and the dummy-derivative method, on
  go-symbolic equations.
- Structural analysis and block-lower-triangular ordering (Tarjan's strongly
  connected components), which also finds algebraic loops.
- Emission of Go through go-symbolic's `codegen`.
- A Modelica-subset reader, last. Full Modelica compatibility is out of reach
  and will be said so in the README.

## References

| Subject | Reference |
| --- | --- |
| index reduction | Pantelides, SIAM J. Sci. Stat. Comput. 9(2), 1988, doi:10.1137/0909014; Mattsson and Soderlind, SIAM J. Sci. Comput. 14(3), 1993, doi:10.1137/0914043 |
| block ordering | Tarjan, SIAM J. Comput. 1(2), 1972, doi:10.1137/0201010 |
| language | the [Modelica Language Specification 3.6](https://specification.modelica.org/), as target vocabulary only |

## How it will be validated

| Area | Criterion |
| --- | --- |
| DAE and modelling | detected index, constraint drift and final-time error against Modelica reference runs |

The corpus is the [Modelica Standard Library](https://github.com/modelica/ModelicaStandardLibrary)
examples (BSD-3-Clause). OpenModelica (OSMC-PL and GPL-3) is an oracle only and
is never ported; Maple is proprietary and is never run as an oracle. Every item
also needs unit tests at 100% coverage and a performance table against the
reference.
