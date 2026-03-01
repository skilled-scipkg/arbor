---
name: arbor-cpp
description: This skill should be used when users ask about cpp in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: Cpp

## High-Signal Playbook
### Route conditions
- Use this skill for user-facing C++ API patterns: `arb::recipe`, `arb::simulation`, labels, mechanisms, domain decomposition (`doc/cpp/index.rst`).
- Route to `arbor-build-and-install` for compiler/CMake issues.
- Route to `arbor-simulation-workflows` for run/reproducibility/performance orchestration.
- Route to `arbor-inputs-and-modeling` for detailed morphology/decor modeling choices.

### Triage questions
- Is this local simulation or distributed/MPI/GPU (`doc/cpp/hardware.rst`)?
- Is the question recipe design, cell specification, interconnectivity, or sampling?
- Are recipe methods thread-safe and side-effect free (`doc/cpp/recipe.rst` warning)?
- Is the failure in label expressions, mechanism assignment, or domain decomposition?
- Are users trying to mirror a Python example in C++ (or vice versa)?

### Canonical workflow
1. Start with `doc/cpp/index.rst` and open the exact API chapter needed.
2. Define/verify recipe required methods (`num_cells`, `get_cell_kind`, `get_cell_description`).
3. Build context and domain decomposition, then instantiate simulation (`doc/cpp/simulation.rst`).
4. Add spike callbacks/samplers only after baseline run compiles.
5. For distributed/GPU, set `proc_allocation` and environment strategy explicitly (`doc/cpp/hardware.rst`).
6. Escalate to implementation files only for behavior undocumented at API level.

### Minimal working example
```cpp
#include <arbor/context.hpp>
#include <arbor/domain_decomposition.hpp>
#include <arbor/simulation.hpp>

int main() {
    my_recipe recipe; // implements required arb::recipe methods
    arb::context ctx = arb::make_context();
    auto decomp = arb::partition_load_balance(recipe, ctx);
    arb::simulation sim(recipe, decomp, ctx, 42);
    sim.run(100.0, 0.025);
}
```

### Pitfalls and fixes
- Recipe member functions must be thread-safe; avoid mutable shared state in recipe queries (`doc/cpp/recipe.rst`).
- Label dictionary type mismatches (region vs locset) cause runtime errors on application (`doc/cpp/labels.rst`).
- Cyclic label dependencies fail when expressions are resolved, not necessarily at definition time (`doc/cpp/labels.rst`).
- Hardware assumptions (GPU/MPI) must match build capabilities (`doc/cpp/hardware.rst`).
- In distributed runs, callback/sampler behavior depends on rank locality; validate per-rank expectations.

### Convergence/validation checks
- Baseline C++ simulation runs with stable spike/sample counts across reruns with same seed.
- Recipe methods return consistent cell kind/description pairs for each gid.
- Label expressions resolve on the target morphology without exceptions.
- Hardware context reports expected thread/GPU/MPI allocation.

## Scope
- Handle questions about documentation grouped under the 'cpp' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `doc/cpp/index.rst`
- `doc/cpp/labels.rst`
- `doc/cpp/cable_cell_format.rst`
- `doc/cpp/remote.rst`
- `doc/cpp/domdec.rst`
- `doc/cpp/mechanisms.rst`
- `doc/cpp/event_generators.rst`
- `doc/cpp/cell.rst`
- `doc/cpp/spike_source_cell.rst`
- `doc/cpp/lif_cell.rst`
- `doc/cpp/interconnectivity.rst`
- `doc/cpp/adex_cell.rst`
- `doc/cpp/simulation.rst`
- `doc/cpp/hardware.rst`
- `doc/cpp/recipe.rst`

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
- `arbor/include/arbor/recipe.hpp`
- `arbor/include/arbor/simulation.hpp`
- `arbor/include/arbor/context.hpp`
- `arbor/simulation.cpp`
- `arbor/domain_decomposition.cpp`
- `arbor/cell_group_factory.cpp`
- `arbor/cable_cell_group.cpp`
- `arbor/lif_cell_group.cpp`
- `arbor/adex_cell_group.cpp`
- `arbor/spike_source_cell_group.cpp`
- `arbor/spike_event_io.cpp`
- `arborenv/default_env.cpp`
- `arborio/cableio.cpp`
- `modcc/modcc.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
