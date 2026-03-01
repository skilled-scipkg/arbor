---
name: arbor-index
description: This skill should be used when users ask how to use arbor and the correct generated documentation skill must be selected before going deeper into source code.
---

# arbor Skills Index

## Route the request
- Always route by user intent first; do not deep-dive source code before opening the best-matching docs skill.
- Prefer documentation-first lookup (`doc/*`, `example/*`, `python/example/*`) and escalate to source only when docs are ambiguous.

### Intent router (first choice)
- Build/install/toolchain/package manager: `arbor-build-and-install`
- Python API, recipes, scripting, probes: `arbor-api-and-scripting`
- Recipe-to-run execution, outputs, reproducibility: `arbor-simulation-workflows`
- MPI/thread/GPU setup and scaling: `arbor-parallel-hpc`
- Errors/debug signatures and test-backed fixes: `arbor-troubleshooting`
- Niche or low-frequency docs (release/dev index/requirements/validation overview): `arbor-advanced-topics`

### Secondary router
- First-run orientation: `arbor-getting-started`
- Worked walkthrough selection: `arbor-examples-and-tutorials`
- Model construction and parameterization: `arbor-inputs-and-modeling`
- C++ API specifics: `arbor-cpp`
- Concepts and theory: `arbor-concepts`, `arbor-theory-and-methods`
- Internal developer implementation docs: `arbor-dev`
- File formats and serialization: `arbor-fileformat`

## Generated topic skills
- `arbor-build-and-install`: build, installation, compilation, and environment setup
- `arbor-api-and-scripting`: language bindings, APIs, and programmatic interfaces
- `arbor-simulation-workflows`: simulation setup, execution flow, and runtime controls
- `arbor-parallel-hpc`: MPI/OpenMP/GPU execution, scaling, and batch systems
- `arbor-troubleshooting`: known issues, diagnostics, and debugging patterns
- `arbor-getting-started`: initial setup, quickstarts, and core concepts
- `arbor-examples-and-tutorials`: worked examples, tutorials, and cookbook usage
- `arbor-inputs-and-modeling`: inputs, system setup, models, and parameterization
- `arbor-cpp`: C++ API and implementation-facing usage
- `arbor-concepts`: concept-level model semantics
- `arbor-theory-and-methods`: numerical/theoretical method notes
- `arbor-dev`: developer internals and extension notes
- `arbor-fileformat`: file format specifics (SWC/NeuroML/NMODL/serdes)
- `arbor-advanced-topics`: consolidated low-signal one-doc advanced references

## Documentation-first inputs
- `doc`

## Tutorials and examples roots
- `example`
- `python/example`

## Test roots for behavior checks
- `test`
- `validation`
- `python/test`

## Escalate only when needed
1. Use the selected topic skill's `Primary documentation references`.
2. If needed, consult that skill's `references/doc_map.md`.
3. Only then inspect its `references/source_map.md` and concrete source entry points.
4. Use targeted symbol search while inspecting source:
   `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`

## Source directories for deeper inspection
- `arbor`
- `arborenv`
- `arborio`
- `lmorpho`
- `mechanisms`
- `modcc`
- `python`
- `sup`
