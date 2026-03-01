---
name: arbor-simulation-workflows
description: This skill should be used when users ask about simulation workflows in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: Simulation Workflows

## High-Signal Playbook
### Route conditions
- Use this skill for recipe-to-run execution flow, runtime controls, output collection, reproducibility, and run-variant comparison (`doc/python/simulation.rst`, `doc/concepts/simulation.rst`, `example/dryrun/readme.md`).
- Route to `arbor-inputs-and-modeling` for cell/parameter construction details.
- Route to `arbor-api-and-scripting` for Python API method semantics.
- Route to `arbor-parallel-hpc` for MPI/thread/GPU placement/scaling tuning.

### Triage questions
- Is the run single-cell, network, or synthetic benchmark (`example/single/README.md`, `example/brunel/readme.md`)?
- Is this local, MPI, GPU, or dry-run emulation (`example/dryrun/readme.md`, `doc/tutorial/network_ring_gpu.rst`)?
- Which outputs are required: spikes, sampled probes, profile meters, files?
- What dt/tfinal/schedule settings define numerical/throughput cost?
- Do you need reproducible reruns (fixed seed, frozen params, deterministic command line)?
- Is the objective correctness, performance diagnosis, or both?

### Canonical workflow
1. Start from a closest shipped workflow (`example/single`, `example/dryrun`, `example/drybench`, `example/brunel`).
2. Define recipe/cell and explicit run controls (tfinal, dt, schedules) (`doc/python/simulation.rst`).
3. Enable required outputs early: spike recording, probe handles, optional profiler/meter checkpoints (`doc/cpp/profiler.rst`, `doc/tutorial/network_ring_gpu.rst`).
4. Run a minimal baseline case and store outputs/params side-by-side.
5. Add complexity (MPI/GPU/network size) one axis at a time.
6. Re-run with the same seed/config to validate reproducibility before scaling.

### Minimal working example
```json
{
  "name": "dry run test",
  "dry-run": true,
  "num-cells-per-rank": 1000,
  "num-ranks": 2,
  "duration": 100,
  "min-delay": 1,
  "depth": 5,
  "branch-probs": [1.0, 0.5],
  "compartments": [100, 2]
}
```

```bash
# Docs: example/dryrun/readme.md
./bench.exe params.json
# Compare against equivalent MPI parameterization and verify spike output equivalence.
```

### Pitfalls and fixes
- Dry-run does not benchmark MPI library scaling itself; it emulates communication costs (`example/drybench/readme.md`).
- Forgetting to enable spike recording yields empty spike output (`doc/python/simulation.rst`).
- Overly coarse dt changes spike timing/shape; tighten dt and compare.
- Under MPI, non-local sample handles can return empty data; gather per-rank results (`doc/python/simulation.rst`).
- GPU tutorial path assumes a GPU-enabled build and correct context selection (`doc/tutorial/network_ring_gpu.rst`).
- Comparing runs with changed seeds/params invalidates reproducibility checks.

### Convergence/validation checks
- Re-run with identical params/seed and compare spike counts/timing and probe traces.
- For dry-run vs equivalent MPI setup, verify equivalent spike outputs as documented (`example/dryrun/readme.md`).
- Track profiler/meter checkpoints (`recipe-create`, `simulation-run`, etc.) to detect workflow regressions (`doc/tutorial/network_ring_gpu.rst`).
- Keep dt/min-delay and network parameters explicit in saved config files.

## Scope
- Handle questions about simulation setup, execution flow, and runtime controls.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `example/lfp/README.md`
- `example/drybench/readme.md`
- `example/dryrun/readme.md`
- `example/v_clamp/README.md`
- `example/single/README.md`
- `example/remote/readme.md`
- `example/brunel/readme.md`
- `doc/tutorial/single_cell_gui.rst`
- `doc/contrib/pr.rst`
- `doc/tutorial/network_ring_gpu.rst`
- `doc/concepts/decor.rst`
- `doc/cpp/profiler.rst`
- `doc/python/simulation.rst`
- `doc/concepts/simulation.rst`

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
- `arbor/simulation.cpp`
- `arbor/network.cpp`
- `arbor/network_impl.cpp`
- `arbor/symmetric_recipe.cpp`
- `arbor/communication/dry_run_context.cpp`
- `arbor/profile/profiler.cpp`
- `arbor/memory/gpu_wrappers.cpp`
- `python/simulation.cpp`
- `python/network.cpp`
- `python/mpi.cpp`
- `python/remote.cpp`
- `arborenv/private_gpu.cpp`
- `arborio/networkio.cpp`
- `modcc/errorvisitor.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
