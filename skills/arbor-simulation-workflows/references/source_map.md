# arbor source map: Simulation Workflows

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
- `brunel`
- `cable`
- `cell`
- `cells`
- `clamp`
- `concepts`
- `connectivity`
- `contrib`
- `cpp`
- `decor`
- `detailed`
- `diffusion`
- `drybench`
- `dryrun`
- `dynamics`
- `feature`
- `full`
- `gap`
- `gpu`
- `gui`
- `hardware`
- `integrator`
- `junctions`
- `lfp`
- `network`
- `pipeline`
- `profiler`
- `recipe`
- `remote`
- `ring`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- `rg -n "class|def|struct|namespace" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `python/single_cell_model.cpp` | score: 15 | matched tokens: cell, cpp, single
- `python/cable_cell_io.cpp` | score: 15 | matched tokens: cable, cell, cpp
- `arbor/cable_cell_param.cpp` | score: 15 | matched tokens: cable, cell, cpp
- `arbor/cable_cell_group.cpp` | score: 15 | matched tokens: cable, cell, cpp
- `arbor/cable_cell.cpp` | score: 15 | matched tokens: cable, cell, cpp
- `python/simulation.cpp` | score: 12 | matched tokens: cpp, simulation
- `python/network.cpp` | score: 12 | matched tokens: cpp, network, two
- `python/cells.cpp` | score: 12 | matched tokens: cell, cells, cpp
- `arbor/simulation.cpp` | score: 12 | matched tokens: cpp, simulation
- `arbor/network_impl.cpp` | score: 12 | matched tokens: cpp, network, two
- `arbor/network.cpp` | score: 12 | matched tokens: cpp, network, two
- `arbor/communication/dry_run_context.cpp` | score: 12 | matched tokens: cpp, run
- `python/remote.cpp` | score: 10 | matched tokens: cpp, remote
- `python/recipe.cpp` | score: 10 | matched tokens: cpp, recipe
- `python/profiler.cpp` | score: 10 | matched tokens: cpp, profiler
- `arbor/spike_source_cell_group.cpp` | score: 10 | matched tokens: cell, cpp
- `arborenv/private_gpu.cpp` | score: 10 | matched tokens: cpp, gpu
- `arborenv/gpu_uuid.cpp` | score: 10 | matched tokens: cpp, gpu
- `arbor/symmetric_recipe.cpp` | score: 10 | matched tokens: cpp, recipe
- `arbor/lif_cell_group.cpp` | score: 10 | matched tokens: cell, cpp
- `arbor/gpu_context.cpp` | score: 10 | matched tokens: cpp, gpu
- `arbor/fvm_lowered_cell_impl.cpp` | score: 10 | matched tokens: cell, cpp
- `arbor/cell_group_factory.cpp` | score: 10 | matched tokens: cell, cpp
- `arbor/cable_cell_group.hpp` | score: 10 | matched tokens: cable, cell
- `arbor/benchmark_cell_group.cpp` | score: 10 | matched tokens: cell, cpp
- `arbor/adex_cell_group.cpp` | score: 10 | matched tokens: cell, cpp
- `arbor/profile/profiler.cpp` | score: 10 | matched tokens: cpp, profiler
- `arbor/memory/gpu_wrappers.cpp` | score: 10 | matched tokens: cpp, gpu
- `arbor/hardware/memory.cpp` | score: 10 | matched tokens: cpp, hardware
- `arbor/include/arbor/cable_cell_param.hpp` | score: 10 | matched tokens: cable, cell
