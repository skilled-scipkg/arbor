# arbor source map: Getting Started

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
- `quickstart`
- `single cell`
- `recipe`
- `context`
- `simulation`
- `nmodl`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- `rg -n "class|def|struct|namespace" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `python/example/single_cell_model.py` | Minimal runnable example used in first-run docs.
- `python/example/single_cell_recipe.py` | Recipe-based first simulation example.
- `python/single_cell_model.cpp` | Python single-cell model binding behavior.
- `python/recipe.cpp` | Recipe API binding behavior.
- `python/simulation.cpp` | Simulation API binding behavior.
- `arbor/include/arbor/context.hpp` | Hardware/runtime context API for first simulations.
- `arbor/include/arbor/simulation.hpp` | C++ simulation API contract.
- `arbor/domain_decomposition.cpp` | Domain decomposition used by default workflows.
- `arbor/partition_load_balance.cpp` | Cell partitioning defaults.
- `arbor/cv_policy.cpp` | Discretization defaults and policies.
- `arborio/cableio.cpp` | Morphology load path used by many tutorials.
- `modcc/modcc.cpp` | Mechanism compilation entrypoint (`nmodl` quickstart context).
