# arbor source map: API and Scripting

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
- `abi`
- `bindings`
- `bluepyopt`
- `cable`
- `cell`
- `class`
- `concepts`
- `contrib`
- `cpp`
- `dev`
- `fileformat`
- `function`
- `hardware`
- `interface`
- `l5pc`
- `library`
- `mechanism`
- `mechanisms`
- `morphology`
- `nmodl`
- `probe`
- `profiler`
- `recipe`
- `remote`
- `sample`
- `scripting`
- `shared`
- `simd`
- `simplecell`
- `single`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- `rg -n "class|def|struct|namespace" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `python/single_cell_model.cpp` | score: 23 | matched tokens: cell, cpp, single
- `python/cable_cell_io.cpp` | score: 23 | matched tokens: cable, cell, cpp
- `python/remote.cpp` | score: 18 | matched tokens: cpp, remote
- `python/recipe.cpp` | score: 18 | matched tokens: cpp, recipe
- `python/profiler.cpp` | score: 18 | matched tokens: cpp, profiler
- `python/morphology.cpp` | score: 18 | matched tokens: cpp, morphology
- `python/mechanism.cpp` | score: 18 | matched tokens: cpp, mechanism
- `python/probes.cpp` | score: 15 | matched tokens: cpp, probe
- `python/cells.cpp` | score: 15 | matched tokens: cell, cpp
- `arbor/cable_cell_param.cpp` | score: 15 | matched tokens: cable, cell, cpp
- `arbor/cable_cell_group.cpp` | score: 15 | matched tokens: cable, cell, cpp
- `arbor/cable_cell.cpp` | score: 15 | matched tokens: cable, cell, cpp
- `arbor/backends/multicore/shared_state.cpp` | score: 15 | matched tokens: cpp, shared, state
- `arbor/backends/gpu/shared_state.cpp` | score: 15 | matched tokens: cpp, shared, state
- `python/simulation.cpp` | score: 13 | matched tokens: cpp
- `python/domain_decomposition.cpp` | score: 13 | matched tokens: cpp
- `python/units.cpp` | score: 13 | matched tokens: cpp
- `python/schedule.cpp` | score: 13 | matched tokens: cpp
- `python/recipe.hpp` | score: 13 | matched tokens: recipe
- `python/pyarb.cpp` | score: 13 | matched tokens: cpp
- `python/network.cpp` | score: 13 | matched tokens: cpp
- `python/mpi.cpp` | score: 13 | matched tokens: cpp
- `python/label_dict.cpp` | score: 13 | matched tokens: cpp
- `python/identifiers.cpp` | score: 13 | matched tokens: cpp
- `python/event_generator.cpp` | score: 13 | matched tokens: cpp
- `python/error.cpp` | score: 13 | matched tokens: cpp
- `python/env.cpp` | score: 13 | matched tokens: cpp
- `python/context.cpp` | score: 13 | matched tokens: cpp
- `python/config.cpp` | score: 13 | matched tokens: cpp
- `python/__init__.py` | score: 11
