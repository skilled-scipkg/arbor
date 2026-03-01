# arbor source map: Troubleshooting

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
- `contrib`
- `debug`
- `dev`
- `error`
- `failure`
- `faq`
- `issue`
- `known`
- `problem`
- `troubleshoot`
- `troubleshooting`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- `rg -n "class|def|struct|namespace" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `python/error.hpp` | score: 5 | matched tokens: error
- `python/error.cpp` | score: 5 | matched tokens: error
- `modcc/error.hpp` | score: 5 | matched tokens: error
- `arborio/debug.cpp` | score: 5 | matched tokens: debug
- `arbor/communication/mpi_error.cpp` | score: 5 | matched tokens: error
- `arborio/include/arborio/debug.hpp` | score: 5 | matched tokens: debug
- `arbor/include/arbor/communication/mpi_error.hpp` | score: 5 | matched tokens: error
- `modcc/errorvisitor.hpp` | score: 2 | matched tokens: error
- `modcc/errorvisitor.cpp` | score: 2 | matched tokens: error
- `arbor/memory/device_coordinator.hpp` | score: 2 | matched tokens: dev
