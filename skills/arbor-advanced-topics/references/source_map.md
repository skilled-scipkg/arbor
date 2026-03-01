# arbor source map: Advanced Topics

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
- `advanced`
- `developer`
- `release`
- `requirements`
- `validation`
- `version`
- `environment`
- `debug`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- `rg -n "class|def|struct|namespace" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `validation/CMakeLists.txt` | validation data generation target wiring
- `test/CMakeLists.txt` | test target structure and dependencies
- `arbor/version.cpp` | runtime version/build information plumbing
- `arbor/util/config.hpp` | compile-time feature/config macros
- `arborenv/read_envvar.cpp` | environment variable parsing defaults
- `arborenv/arbenvexcept.cpp` | arborenv exception surfaces
- `python/env.cpp` | Python exposure of environment/config helpers
- `python/error.cpp` | Python-facing exception translation
- `arborio/debug.cpp` | debug helpers for arborio
- `modcc/errorvisitor.cpp` | mechanism compiler error traversal and reporting
- `modcc/error.hpp` | mechanism compiler error types
- `scripts/create_tarball` | release packaging utility referenced in release docs
