---
name: arbor-getting-started
description: This skill should be used when users ask about getting started in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: Getting Started

## High-Signal Playbook
### Route conditions
- Use this skill for first successful simulation, core vocabulary, and quickstart routing.
- Route to `arbor-build-and-install` if import/build/toolchain steps fail first.
- Route to `arbor-inputs-and-modeling` when morphology/decor parameterization becomes the main issue.

### Minimal command/input
```bash
python - <<'PY'
import arbor as A
from arbor import units as U
tree = A.segment_tree()
tree.append(A.mnpos, A.mpoint(-3, 0, 0, 3), A.mpoint(3, 0, 0, 3), tag=1)
labels = A.label_dict({"soma": "(tag 1)", "mid": "(location 0 0.5)"})
decor = A.decor().paint('"soma"', A.density("hh")).place('"mid"', A.threshold_detector(-10*U.mV), "sd")
cell = A.cable_cell(tree, decor, labels)
m = A.single_cell_model(cell)
m.probe("voltage", '"mid"', tag="Um", frequency=10*U.kHz)
m.run(10*U.ms, 0.025*U.ms)
print(len(m.traces), len(m.spikes))
PY
```

### Validation checkpoints
- Run returns at least one trace and no construction/runtime exceptions.
- `dt`, `tfinal`, and probe location are explicit in the command for reproducibility.
- If this baseline fails, capture the exact command + traceback and route to `arbor-troubleshooting`.

## Scope
- Handle questions about initial setup, quickstarts, and core concepts.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `doc/concepts/index.rst`
- `doc/tutorial/nmodl.rst`
- `doc/tutorial/cosim.rst`
- `doc/tutorial/single_cell_model.rst`

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
- `python/example/single_cell_model.py`
- `python/example/single_cell_recipe.py`
- `python/single_cell_model.cpp`
- `python/recipe.cpp`
- `python/simulation.cpp`
- `arbor/include/arbor/context.hpp`
- `arbor/include/arbor/simulation.hpp`
- `arbor/domain_decomposition.cpp`
- `arbor/partition_load_balance.cpp`
- `arbor/cv_policy.cpp`
- `arborio/cableio.cpp`
- `modcc/modcc.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
