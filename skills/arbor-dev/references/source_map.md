# arbor source map: Dev

Generated from source roots:
- `arbor`
- `arborenv`
- `arborio`
- `lmorpho`
- `mechanisms`
- `modcc`
- `python`
- `sup`

Use this map only after exhausting the topic docs in `references/doc_map.md`.

## Topic query tokens
- `dev`
- `export`
- `cell groups`
- `catalogues`
- `util`
- `extension`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- `rg -n "class|def|struct|namespace" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `arbor/include/arbor/mechcat.hpp` | Mechanism catalogue API used in extension workflows.
- `arbor/mechcat.cpp` | Built-in catalogue wiring and runtime registration.
- `python/mechanism.cpp` | Python binding for catalogue extension.
- `mechanisms/CMakeLists.txt` | Add/build catalogue definitions from source.
- `mechanisms/BuildModules.cmake` | Mechanism build helper logic.
- `arbor/cell_group_factory.cpp` | Cell-group creation and dispatch rules.
- `arbor/cable_cell_group.cpp` | Cable cell group implementation used in dev docs.
- `arbor/backends/multicore/shared_state.cpp` | CPU shared-state layout for grouped cells.
- `arbor/backends/gpu/shared_state.cpp` | GPU shared-state host-side plumbing.
- `arbor/include/arbor/util/unique_any.hpp` | Developer utility type used in APIs.
- `arbor/include/arbor/util/any_ptr.hpp` | Runtime pointer-erasure utility.
- `arbor/include/arbor/util/any_cast.hpp` | Utility cast helpers referenced by util docs.
- `python/util.hpp` | Python-facing utility wrappers.
- `modcc/util.hpp` | Mechanism-compiler utility helpers.
