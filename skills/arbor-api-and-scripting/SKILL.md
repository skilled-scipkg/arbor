---
name: arbor-api-and-scripting
description: This skill should be used when users ask about api and scripting in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: API and Scripting

## High-Signal Playbook
### Route conditions
- Use this skill for Python API design/usage, recipe construction, probes/samplers, event generators, and runtime API wiring (`doc/python/index.rst`, `doc/python/recipe.rst`, `doc/python/simulation.rst`).
- Route to `arbor-inputs-and-modeling` for model-physics/parameterization decisions.
- Route to `arbor-cpp` for user-facing C++ API design and idioms.
- Route to `arbor-build-and-install` if API usage is blocked by missing compile-time features (MPI/GPU/catalogues).

### Triage questions
- Is this single-cell (`single_cell_model`) or full network (`recipe` + `simulation`)?
- Need spike recording, probe sampling, or both (`doc/python/simulation.rst`)?
- Are units and schedules consistent (`doc/python/recipe.rst`, `doc/python/event_generators.rst`)?
- Is MPI/GPU required and actually enabled in the build (`doc/python/hardware.rst`)?
- Is there a custom mechanism catalogue or only built-ins (`doc/fileformat/nmodl.rst`)?
- Is the target behavior from a documented example/test that can be mirrored first?

### Canonical workflow
1. Start with `doc/python/index.rst` and route to the exact API doc page (recipe/simulation/probes/hardware).
2. Build the smallest working model first (`doc/python/single_cell_model.rst` or `python/example/single_cell_recipe.py`).
3. Add recording/sampling and verify output shapes/types (`doc/python/simulation.rst`).
4. Add event generators/schedules only after baseline run is correct (`doc/python/recipe.rst`).
5. Confirm build-time capabilities with `arbor.config()` before enabling MPI/GPU code paths (`doc/python/hardware.rst`).
6. Escalate to C++ binding/source only for behavior not resolved by docs.

### Minimal working example
```python
import arbor as A
from arbor import units as U

class one_cell(A.recipe):
    def __init__(self, cell):
        A.recipe.__init__(self)
        self.cell = cell
        self.props = A.neuron_cable_properties()
    def num_cells(self): return 1
    def cell_kind(self, gid): return A.cell_kind.cable
    def cell_description(self, gid): return self.cell
    def probes(self, gid): return [A.cable_probe_membrane_voltage('"midpoint"', "Um")]
    def global_properties(self, kind): return self.props

m = A.segment_tree(); m.append(A.mnpos, A.mpoint(-3,0,0,3), A.mpoint(3,0,0,3), tag=1)
labels = A.label_dict({"midpoint": "(location 0 0.5)", "soma": "(tag 1)"})
decor = A.decor().paint('"soma"', A.density("hh")).place('"midpoint"', A.threshold_detector(-10*U.mV), "sd")
sim = A.simulation(one_cell(A.cable_cell(m, decor, labels)))
sim.record(A.spike_recording.all)
h = sim.sample((0, "Um"), A.regular_schedule(0.1*U.ms))
sim.run(30*U.ms)
print(len(sim.spikes()), len(sim.samples(h)))
```

### Pitfalls and fixes
- Missing `A.recipe.__init__(self)` in subclass constructor causes subtle binding issues (`doc/python/recipe.rst`).
- No spikes returned because recording policy not enabled (`doc/python/simulation.rst`: call `sim.record(...)`).
- Confusing sample frequency with schedule interval: `regular_schedule` takes timestep-like spacing (`doc/python/recipe.rst`, `doc/python/simulation.rst`).
- `cell_kind`/`cell_description` mismatch for a gid causes model-construction failures (`doc/python/recipe.rst`).
- MPI/GPU API calls fail when build lacks those features; check `arbor.config()` first (`doc/python/hardware.rst`).
- Custom mechanism scripts fail without catalogue build/load alignment (`doc/fileformat/nmodl.rst`, `python/example/ou_lif/ou_lif.py`).

### Convergence/validation checks
- `arbor.config()` and `A.print_config()` reflect expected compile flags (`doc/python/hardware.rst`).
- `sim.spikes()` ordering/type matches doc contract (`doc/python/simulation.rst`).
- Probe sample payload shape is stable across reruns with fixed configuration.
- For distributed runs, account for rank-local sample empties on non-local gids (`doc/python/simulation.rst`).

## Scope
- Handle questions about language bindings, APIs, and programmatic interfaces.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `doc/python/index.rst`
- `python/example/single_cell_bluepyopt/simplecell/Readme.md`
- `python/example/single_cell_bluepyopt/l5pc/Readme.md`
- `doc/python/probe_sample.rst`
- `doc/fileformat/nmodl.rst`
- `doc/fileformat/cable_cell.rst`
- `doc/dev/simd_api.rst`
- `doc/cpp/probe_sample.rst`
- `doc/contrib/test.rst`
- `doc/dev/mechanism_abi.rst`
- `doc/python/recipe.rst`
- `doc/python/morphology.rst`
- `doc/python/simulation.rst`
- `doc/python/hardware.rst`

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
- `python/single_cell_model.cpp`
- `python/recipe.cpp`
- `python/simulation.cpp`
- `python/event_generator.cpp`
- `python/probes.cpp`
- `python/mechanism.cpp`
- `python/morphology.cpp`
- `arbor/simulation.cpp`
- `arbor/cable_cell_group.cpp`
- `arbor/backends/multicore/shared_state.cpp`
- `arbor/backends/gpu/shared_state.cpp`
- `arborenv/default_env.cpp`
- `arborio/cableio.cpp`
- `modcc/modcc.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
