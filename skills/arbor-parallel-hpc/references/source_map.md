# arbor source map: Parallel and HPC

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
- `parallel`
- `mpi`
- `openmp`
- `gpu`
- `scaling`
- `load balance`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- `rg -n "class|def|struct|namespace" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `arbor/communication/mpi.cpp` | MPI communicator integration.
- `arbor/communication/mpi_context.cpp` | MPI context creation and rank behavior.
- `arbor/communication/dry_run_context.cpp` | Dry-run backend for distributed workflow checks.
- `arbor/gpu_context.cpp` | GPU context selection and device wiring.
- `arbor/memory/gpu_wrappers.cpp` | GPU memory wrapper behavior used in runtime execution.
- `arbor/backends/gpu/matrix_state_fine.hpp` | GPU matrix state in cable solve.
- `arbor/backends/gpu/matrix_fine.cu` | GPU cable solve kernels.
- `arbor/backends/gpu/shared_state.cu` | GPU shared-state update kernels.
- `arbor/backends/multicore/shared_state.cpp` | CPU/OpenMP shared-state behavior.
- `python/mpi.cpp` | Python MPI-facing bindings.
- `python/network.cpp` | Python network flow used in MPI tutorials.
- `arbor/network_impl.cpp` | Runtime network execution implementation.
- `arbor/partition_load_balance.cpp` | Partitioning and placement logic.
- `arborenv/private_gpu.cpp` | GPU environment probing.
- `arborenv/include/arborenv/with_mpi.hpp` | MPI feature gating.
- `arbor/include/arbor/gpu/gpu_api.hpp` | GPU API surface.
- `arbor/include/arbor/gpu/cuda_api.hpp` | CUDA backend API surface.
- `arbor/include/arbor/gpu/hip_api.hpp` | HIP backend API surface.
