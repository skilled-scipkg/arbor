# arbor source map: Fileformat

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
- `fileformat`
- `swc`
- `neuroml`
- `asc`
- `nmodl`
- `serdes`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- `rg -n "class|def|struct|namespace" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `arbor/include/arbor/serdes.hpp` | Core serialization/checkpoint interface.
- `arborio/include/arborio/json_serdes.hpp` | JSON-backed serialization helpers.
- `arborio/include/arborio/cableio.hpp` | Cable-cell I/O API.
- `arborio/cableio.cpp` | Cable-cell file I/O behavior.
- `arborio/include/arborio/swcio.hpp` | SWC loader API.
- `arborio/swcio.cpp` | SWC parser implementation.
- `arborio/include/arborio/neuroml.hpp` | NeuroML loader API.
- `arborio/neuroml.cpp` | NeuroML read path implementation.
- `arborio/include/arborio/neurolucida.hpp` | ASC/Neurolucida loader API.
- `arborio/neurolucida.cpp` | ASC/Neurolucida parser implementation.
- `arborio/nml_parse_morphology.cpp` | Morphology parsing used by NeuroML flow.
- `arborio/cv_policy_parse.cpp` | File-driven CV policy parsing.
- `python/cable_cell_io.cpp` | Python exposure of morphology/fileformat loaders.
- `python/mechanism.cpp` | Python mechanism catalogue and fileformat-facing bindings.
- `modcc/modcc.cpp` | NMODL compiler entrypoint.
- `modcc/parser.cpp` | NMODL parser implementation details.
