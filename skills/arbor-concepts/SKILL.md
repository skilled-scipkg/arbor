---
name: arbor-concepts
description: This skill should be used when users ask about concepts in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: Concepts

## High-Signal Playbook
### Route conditions
- Use this skill for discretization and interconnectivity semantics from concept docs.
- Route to `arbor-api-and-scripting` or `arbor-cpp` for API-call syntax questions.
- Route to `arbor-simulation-workflows` when the request shifts to runtime orchestration/profiling.

### Minimal command/input
```bash
python - <<'PY'
import arbor as A
from arbor import units as U
tree = A.segment_tree()
tree.append(A.mnpos, A.mpoint(-3, 0, 0, 3), A.mpoint(3, 0, 0, 3), tag=1)
labels = A.label_dict({"soma": "(tag 1)", "mid": "(location 0 0.5)"})
decor = A.decor().paint('"soma"', A.density("hh")).place('"mid"', A.threshold_detector(-10*U.mV), "sd")
cell = A.cable_cell(tree, decor, labels, A.cv_policy_max_extent(10))
class one(A.recipe):
    def __init__(self): A.recipe.__init__(self); self.props = A.neuron_cable_properties()
    def num_cells(self): return 1
    def cell_kind(self, gid): return A.cell_kind.cable
    def cell_description(self, gid): return cell
    def probes(self, gid): return [A.cable_probe_membrane_voltage('"mid"', "Um")]
    def global_properties(self, kind): return self.props
sim = A.simulation(one())
h = sim.sample((0, "Um"), A.regular_schedule(0.1*U.ms))
sim.run(5*U.ms)
print(len(sim.samples(h)[0][0]))
PY
```

### Validation checkpoints
- Simulation runs with an explicit CV policy and returns non-empty sample data.
- Connectivity/discretization edits are checked by comparing the same observable before and after the change.

## Scope
- Handle questions about documentation grouped under the 'concepts' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `doc/concepts/interconnectivity.rst`
- `doc/concepts/discretization.rst`

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
- `arbor/include/arbor/simulation.hpp`
- `arbor/simulation.cpp`
- `arbor/include/arbor/domain_decomposition.hpp`
- `arbor/domain_decomposition.cpp`
- `arbor/partition_load_balance.cpp`
- `arbor/include/arbor/network.hpp`
- `arbor/network.cpp`
- `arbor/network_impl.cpp`
- `arbor/connection.hpp`
- `arbor/spike_event_io.cpp`
- `arbor/include/arbor/cv_policy.hpp`
- `arbor/cv_policy.cpp`
- `python/simulation.cpp`
- `python/network.cpp`
- `python/domain_decomposition.cpp`
- `python/recipe.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
