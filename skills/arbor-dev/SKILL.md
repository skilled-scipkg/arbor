---
name: arbor-dev
description: This skill should be used when users ask about dev in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: Dev

## High-Signal Playbook
### Route conditions
- Use this skill for internal extension work: cell-group internals, catalogue extension, symbol/export conventions, and utility wrappers.
- Route to `arbor-build-and-install` for general compiler/toolchain setup failures.
- Route to `arbor-troubleshooting` when there is an already reproducible runtime/build error signature.

### Minimal command/input
```bash
# Rebuild mechanisms/catalogues and run the targeted catalogue unit test
cmake -S . -B build -DARB_WITH_PYTHON=ON
cmake --build build -j4 --target mechanisms
python -m pytest -q python/test/unit/test_catalogues.py
```

### Validation checkpoints
- Mechanism/catalogue targets build cleanly after changes in `mechanisms/` or `mechcat` wiring.
- `test_catalogues.py` passes and confirms expected catalogue behavior at the Python boundary.
- Cell-group changes are paired with at least one targeted unit/distributed test run.

## Scope
- Handle questions about documentation grouped under the 'dev' theme.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `doc/dev/export.rst`
- `doc/dev/cell_groups.rst`
- `doc/dev/util.rst`
- `doc/dev/extending_catalogues.rst`

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
- `arbor/include/arbor/mechcat.hpp`
- `arbor/mechcat.cpp`
- `python/mechanism.cpp`
- `mechanisms/CMakeLists.txt`
- `mechanisms/BuildModules.cmake`
- `arbor/cell_group_factory.cpp`
- `arbor/cable_cell_group.cpp`
- `arbor/backends/multicore/shared_state.cpp`
- `arbor/backends/gpu/shared_state.cpp`
- `arbor/include/arbor/util/unique_any.hpp`
- `arbor/include/arbor/util/any_ptr.hpp`
- `arbor/include/arbor/util/any_cast.hpp`
- `python/util.hpp`
- `modcc/util.hpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
