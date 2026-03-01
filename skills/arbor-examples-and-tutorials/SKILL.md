---
name: arbor-examples-and-tutorials
description: This skill should be used when users ask about examples and tutorials in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: Examples and Tutorials

## High-Signal Playbook
### Route conditions
- Use this skill to pick and run the closest shipped example/tutorial before custom development (`doc/tutorial/index.rst`, `example/readme.md`).
- Route to `arbor-simulation-workflows` for production run/restart/output design.
- Route to `arbor-inputs-and-modeling` when the question is about model construction details, not example selection.
- Route to `arbor-api-and-scripting` or `arbor-cpp` when users need API semantics beyond tutorial flow.

### Triage questions
- Do they want Python or C++ examples first (`doc/tutorial/index.rst`, `example/readme.md`)?
- Which domain feature is primary: single-cell, network, diffusion, plasticity, gap junctions, profiling?
- Does the run require MPI/GPU, or must it stay laptop-local?
- Are plotting/analysis extras installed (pandas, seaborn, LFPykit) (`doc/tutorial/index.rst`)?
- Is success criterion “example runs”, “matches expected shape/spikes”, or “performance profile”?

### Canonical workflow
1. Route to the smallest relevant tutorial/example from `doc/tutorial/index.rst` or `example/readme.md`.
2. Run the unmodified example first.
3. Capture baseline outputs (plots, csv, spike files) before edits.
4. Change one axis at a time: morphology, network size, hardware, sampling.
5. If divergence appears, diff against the baseline command/inputs.
6. Escalate to source only for behavior not described by docs or README.

### Minimal working example
```bash
# C++ examples baseline (docs: example/readme.md)
cd arbor
mkdir -p build && cd build
cmake .. -DARB_VECTORIZE=ON -DARB_WITH_MPI=ON -DCMAKE_CXX_COMPILER=$(which g++)
make examples
bin/dryrun
```

```bash
# Python tutorial-style baseline
python python/example/single_cell_model.py
# Produces single_cell_model_result.svg and single_cell_model_result.csv
```

### Pitfalls and fixes
- Missing plotting dependencies causes tutorial scripts to fail; install extras noted in tutorial index (`doc/tutorial/index.rst`).
- Wrong working directory breaks relative data paths in examples; run from repo root or adjust paths.
- GPU/MPI tutorials fail on non-enabled builds; verify install flags before running hardware tutorials (`doc/tutorial/network_ring_gpu.rst`).
- Mixing tutorial concepts without first validating a baseline makes regressions hard to localize.
- Contributor docs are guidance, but runtime/API truth should be cross-checked in concept/API docs.

### Convergence/validation checks
- Baseline example runs end-to-end and produces expected output artifact(s).
- Modified run preserves core invariants (non-empty spikes/traces, plausible voltage ranges).
- For network examples, verify parameter changes are reflected in recorded outputs.
- Keep the exact baseline command line for quick rollback comparison.

## Scope
- Handle questions about worked examples, tutorials, and cookbook usage.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `example/gap_junctions/readme.md`
- `doc/tutorial/index.rst`
- `example/plasticity/readme.md`
- `doc/contrib/index.rst`
- `example/readme.md`
- `example/adex/README.md`
- `example/ring/readme.md`
- `example/ornstein_uhlenbeck/readme.md`
- `example/network_description/readme.md`
- `example/diffusion/README.md`
- `example/busyring/readme.md`
- `example/busyring-tiled/readme.md`
- `doc/tutorial/network_ring.rst`
- `doc/tutorial/plasticity.rst`
- `doc/tutorial/single_cell_cable.rst`

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
- `example/single/single.cpp`
- `example/dryrun/dryrun.cpp`
- `example/drybench/drybench.cpp`
- `example/ring/ring.cpp`
- `example/brunel/brunel.cpp`
- `python/example/single_cell_model.py`
- `python/example/single_cell_recipe.py`
- `python/example/network_ring_gpu.py`
- `arbor/simulation.cpp`
- `arbor/network_impl.cpp`
- `arborio/networkio.cpp`
- `arborenv/private_gpu.cpp`
- `modcc/modcc.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
