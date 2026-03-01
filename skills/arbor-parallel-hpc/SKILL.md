---
name: arbor-parallel-hpc
description: This skill should be used when users ask about parallel and hpc in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: Parallel and HPC

## High-Signal Playbook
### Route conditions
- Use this skill for MPI rank behavior, GPU selection, and scaling-related execution choices.
- Route to `arbor-build-and-install` when MPI/GPU support is missing at build time.
- Route to `arbor-simulation-workflows` for non-HPC workflow orchestration questions.

### Minimal command/input
```bash
# 1) Confirm build supports the intended runtime
python -c "import arbor as A; print(A.config())"

# 2) Run distributed tutorial baseline (requires mpi launcher + pandas)
mpiexec -n 2 python python/example/network_ring_mpi.py
```

### Validation checkpoints
- `A.config()` reports expected MPI/GPU capability before running distributed commands.
- MPI run completes with no rank-local initialization errors.
- Output artifacts (for example `result_mpi_*.csv`) appear for ranks with local cells.

## Scope
- Handle questions about MPI/OpenMP/GPU execution, scaling, and batch systems.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `doc/tutorial/network_ring_mpi.rst`
- `doc/dev/matrix_solver.rst`

## Workflow
- Start with the primary references above.
- If details are missing, inspect `references/doc_map.md` for the complete topic document list.
- Use tutorials/examples as executable usage patterns when available.
- Use tests as behavior or regression references when available.
- If ambiguity remains after docs, inspect `references/source_map.md` and start with the ranked source entry points.
- Cite exact documentation file paths in responses.

## Tutorials and examples
- `example`
- `python/example`

## Test references
- `test`
- `validation`
- `python/test`

## Optional deeper inspection
- `arbor`
- `arborenv`
- `arborio`
- `lmorpho`
- `mechanisms`
- `modcc`
- `python`
- `sup`

## Source entry points for unresolved issues
- `arbor/communication/mpi.cpp`
- `arbor/communication/mpi_context.cpp`
- `arbor/communication/dry_run_context.cpp`
- `arbor/gpu_context.cpp`
- `arbor/memory/gpu_wrappers.cpp`
- `arbor/backends/gpu/matrix_state_fine.hpp`
- `arbor/backends/gpu/matrix_fine.cu`
- `arbor/backends/gpu/shared_state.cu`
- `arbor/backends/multicore/shared_state.cpp`
- `python/mpi.cpp`
- `python/network.cpp`
- `arbor/network_impl.cpp`
- `arbor/partition_load_balance.cpp`
- `arborenv/private_gpu.cpp`
- `arborenv/include/arborenv/with_mpi.hpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
