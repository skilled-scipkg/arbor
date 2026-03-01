# arbor source map: Theory and Methods

Generated from source roots:
- `arbor`
- `arborenv`
- `arborio`
- `lmorpho`
- `mechanisms`
- `modcc`
- `python`
- `sup`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Topic query tokens
- `algorithm`
- `equation`
- `method`
- `numerics`
- `solver`
- `stochastic`
- `sde`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- `rg -n "class|def|struct|namespace" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `arbor/fvm_lowered_cell_impl.cpp` | Main cable-cell time integration path.
- `arbor/fvm_layout.cpp` | Discretized matrix/layout assembly.
- `arbor/backends/multicore/cable_solver.hpp` | CPU cable equation solver interface.
- `arbor/backends/multicore/diffusion_solver.hpp` | CPU diffusion solver interface.
- `arbor/backends/multicore/shared_state.cpp` | CPU backend state update logic.
- `arbor/backends/gpu/matrix_state_fine.hpp` | GPU matrix state used in solver steps.
- `arbor/backends/gpu/matrix_fine.cu` | GPU matrix solve/update kernels.
- `arbor/backends/gpu/shared_state.cu` | GPU shared-state kernel behavior.
- `arbor/backends/gpu/diffusion.cu` | GPU diffusion kernels.
- `arbor/cv_policy.cpp` | Numerical partitioning/discretization behavior.
- `arbor/simulation.cpp` | Time-step loop orchestration.
- `modcc/solvers.cpp` | Mechanism solver generation strategy (`cnexp`, `sparse`, stochastic).
- `modcc/kineticrewriter.cpp` | Kinetic scheme lowering rules.
- `modcc/linearrewriter.cpp` | Linear system rewrite used for solver generation.
- `modcc/symdiff.cpp` | Symbolic differentiation support for generated methods.
