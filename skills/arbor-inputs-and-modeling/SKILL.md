---
name: arbor-inputs-and-modeling
description: This skill should be used when users ask about inputs and modeling in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: Inputs and Modeling

## High-Signal Playbook
### Route conditions
- Use this skill for morphology/labels/decor/cv-policy setup, mechanism parameterization, and model translation from external datasets (`doc/tutorial/single_cell_detailed.rst`, `doc/tutorial/single_cell_allen.rst`, `doc/concepts/recipe.rst`).
- Route to `arbor-simulation-workflows` for runtime/output orchestration.
- Route to `arbor-api-and-scripting` for Python class/method semantics.
- Route to `arbor-fileformat` for SWC/NeuroML/NMODL format-specific interpretation.

### Triage questions
- What is the source of morphology/model input (SWC, JSON fit, hand-built segment tree)?
- Is this cable, LIF, AdEx, spike-source, or benchmark cell type?
- Are labels/regions/locsets already defined and consistent with morphology tags?
- Which mechanisms and ion settings are required, with which units?
- What discretization policy is expected (`cv_policy_*`) and why?
- Is there a reference trace/observable to validate against?

### Canonical workflow
1. Establish morphology source and parser choice (`load_swc_arbor` vs `load_swc_neuron`) from docs/tutorial.
2. Build/validate label dictionary before decorating mechanisms.
3. Apply global properties first, then regional overrides and mechanism placement (`doc/tutorial/single_cell_detailed.rst`).
4. Set CV policy explicitly for reproducibility (`doc/tutorial/single_cell_allen.rst`).
5. Run a minimal probe set and compare to expected physiology/reference.
6. Escalate to source for parser/label-resolution edge cases only.

### Minimal working example
```python
import arbor as A
from arbor import units as U

morph = A.load_swc_arbor("python/example/single_cell_detailed.swc").morphology
labels = A.label_dict({"all": "(all)", "root": "(root)", "mid": "(location 0 0.5)"}).add_swc_tags()
decor = (
    A.decor()
    .set_property(Vm=-55*U.mV, tempK=300*U.Kelvin)
    .paint('"all"', A.density("pas"))
    .paint('"soma"', A.density("hh"))
    .place('"root"', A.threshold_detector(-10*U.mV), "sd")
)
cvp = A.cv_policy_max_extent(20)
cell = A.cable_cell(morph, decor, labels, cvp)
model = A.single_cell_model(cell)
model.probe("voltage", '"mid"', tag="Um", frequency=10*U.kHz)
model.run(30*U.ms, 0.025*U.ms)
print(len(model.traces), len(model.spikes))
```

### Pitfalls and fixes
- SWC interpretation mismatch (`arbor` vs `neuron` semantics) changes geometry behavior (`doc/tutorial/single_cell_allen.rst`, `doc/fileformat/swc.rst`).
- Missing/incorrect labels lead to failed `paint`/`place` resolution; validate label dictionary against morphology (`doc/tutorial/single_cell_detailed.rst`).
- Parameter files may need region/mechanism name normalization (Allen tutorial parser logic).
- Ion reversal behavior (e.g., calcium via Nernst) may require explicit setup to match reference behavior (`doc/tutorial/single_cell_allen.rst`).
- Coarse CV policy can alter numerical behavior; tighten and compare observables (`doc/tutorial/probe_lfpykit.rst`).
- Mechanism catalogue mismatch blocks custom mechanisms (align with `doc/fileformat/nmodl.rst`).

### Convergence/validation checks
- Geometry/labels resolve and probes attach without errors.
- Basic observables (spikes/voltage traces) are non-empty and physiologically plausible.
- Reference comparison (when available, e.g. Allen tutorial) stays within expected qualitative behavior.
- CV policy and key parameters are explicit and version-controlled.

## Scope
- Handle questions about inputs, system setup, models, and physical parameterization.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `python/test/readme.md`
- `doc/ecosystem/index.rst`
- `example/bench/readme.md`
- `doc/features/index.rst`
- `python/example/ou_lif/Readme.md`
- `doc/tutorial/single_cell_allen.rst`
- `doc/tutorial/single_cell_detailed.rst`
- `doc/tutorial/single_cell_bluepyopt.rst`
- `doc/tutorial/probe_lfpykit.rst`
- `doc/concepts/recipe.rst`
- `doc/tutorial/calcium_stdp_curve.rst`
- `doc/python/single_cell_model.rst`
- `doc/fileformat/swc.rst`

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
- `arbor/morph/morphology.cpp`
- `arbor/label_resolution.cpp`
- `arbor/cv_policy.cpp`
- `arbor/cable_cell_param.cpp`
- `arbor/cable_cell_group.cpp`
- `arbor/fvm_lowered_cell_impl.cpp`
- `arborio/nml_parse_morphology.cpp`
- `arborio/cableio.cpp`
- `python/cable_cell_io.cpp`
- `python/morphology.cpp`
- `python/single_cell_model.cpp`
- `modcc/modcc.cpp`
- `arborenv/read_envvar.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
