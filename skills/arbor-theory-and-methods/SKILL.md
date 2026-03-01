---
name: arbor-theory-and-methods
description: This skill should be used when users ask about theory and methods in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: Theory and Methods

## High-Signal Playbook
### Route conditions
- Use this skill for numerics/method questions (`cnexp`, `sparse`, stochastic Euler-Maruyama) and solver behavior interpretation.
- Route to `arbor-inputs-and-modeling` for parameter/model-definition issues.
- Route to `arbor-simulation-workflows` for execution orchestration and profiling questions.

### Minimal command/input
```bash
python - <<'PY'
import arbor as A
from arbor import units as U
def run(dt):
    tree = A.segment_tree()
    tree.append(A.mnpos, A.mpoint(-3, 0, 0, 3), A.mpoint(3, 0, 0, 3), tag=1)
    labels = A.label_dict({"soma": "(tag 1)", "mid": "(location 0 0.5)"})
    decor = A.decor().paint('"soma"', A.density("hh")).place('"mid"', A.threshold_detector(-10*U.mV), "sd")
    m = A.single_cell_model(A.cable_cell(tree, decor, labels))
    m.probe("voltage", '"mid"', tag="Um", frequency=10*U.kHz)
    m.run(20*U.ms, dt)
    return len(m.spikes), len(m.traces[0].value)
print("dt=0.025 ms:", run(0.025*U.ms))
print("dt=0.0125 ms:", run(0.0125*U.ms))
PY
```

### Validation checkpoints
- Both timestep runs complete without solver/runtime errors.
- Observable differences are bounded and explainable when timestep changes.
- If stochastic mechanisms are involved, keep seed/control parameters fixed while comparing methods.

## Scope
- Handle questions about theoretical background and algorithmic methods.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `doc/dev/sde.rst`
- `doc/dev/numerics.rst`

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
- `arbor/fvm_lowered_cell_impl.cpp`
- `arbor/fvm_layout.cpp`
- `arbor/backends/multicore/cable_solver.hpp`
- `arbor/backends/multicore/diffusion_solver.hpp`
- `arbor/backends/multicore/shared_state.cpp`
- `arbor/backends/gpu/matrix_state_fine.hpp`
- `arbor/backends/gpu/matrix_fine.cu`
- `arbor/backends/gpu/shared_state.cu`
- `arbor/backends/gpu/diffusion.cu`
- `arbor/cv_policy.cpp`
- `arbor/simulation.cpp`
- `modcc/solvers.cpp`
- `modcc/kineticrewriter.cpp`
- `modcc/linearrewriter.cpp`
- `modcc/symdiff.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
