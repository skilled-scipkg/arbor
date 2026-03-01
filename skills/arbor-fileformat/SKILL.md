---
name: arbor-fileformat
description: This skill should be used when users ask about fileformat in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: Fileformat

## High-Signal Playbook
### Route conditions
- Use this skill for SWC/NeuroML/ASC/NMODL/serialization interpretation and parser behavior.
- Route to `arbor-inputs-and-modeling` for model-physics choices after files are loaded.
- Route to `arbor-build-and-install` if toolchain/build integration is the blocker.

### Minimal command/input
```bash
python - <<'PY'
import arbor as A
morph = A.load_swc_arbor("python/example/single_cell_detailed.swc").morphology
labels = A.label_dict({"all": "(all)"}).add_swc_tags()
cell = A.cable_cell(morph, A.decor().paint('"all"', A.density("pas")), labels)
print(type(cell).__name__)
PY
```

### Validation checkpoints
- Morphology input parses without exceptions.
- Label resolution and decoration succeed on loaded morphology.
- If mechanism parsing is in question, confirm `modcc` path and mechanism names used by the model.

## Scope
- Handle questions about documentation grouped under the 'fileformat' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `doc/fileformat/index.rst`
- `doc/fileformat/serdes.rst`

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
- `arborio/include/arborio/json_serdes.hpp`
- `arbor/include/arbor/serdes.hpp`
- `arborio/include/arborio/cableio.hpp`
- `arborio/cableio.cpp`
- `arborio/include/arborio/swcio.hpp`
- `arborio/swcio.cpp`
- `arborio/include/arborio/neuroml.hpp`
- `arborio/neuroml.cpp`
- `arborio/include/arborio/neurolucida.hpp`
- `arborio/neurolucida.cpp`
- `arborio/nml_parse_morphology.cpp`
- `arborio/cv_policy_parse.cpp`
- `python/cable_cell_io.cpp`
- `python/mechanism.cpp`
- `modcc/modcc.cpp`
- `modcc/parser.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
