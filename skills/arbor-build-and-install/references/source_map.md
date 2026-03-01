# arbor source map: Build and Install

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
- `build`
- `cmake`
- `cmakelists`
- `code`
- `communication`
- `compile`
- `contrib`
- `cpp`
- `dependencies`
- `dependency`
- `dev`
- `generators`
- `gui`
- `install`
- `installation`
- `make`
- `management`
- `morphology`
- `playground`
- `spack`
- `ubench`
- `unit`
- `validation`
- `version`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- `rg -n "class|def|struct|namespace" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `python/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `sup/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `modcc/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `mechanisms/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `lmorpho/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `arborio/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `arborenv/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `arbor/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `arbor/include/CMakeLists.txt` | score: 19 | matched tokens: cmake, cmakelists, make
- `mechanisms/BuildModules.cmake` | score: 13 | matched tokens: build, cmake, make
- `python/morphology.cpp` | score: 10 | matched tokens: cpp, morphology
- `arborio/nml_parse_morphology.cpp` | score: 10 | matched tokens: cpp, morphology
- `arbor/version.cpp` | score: 10 | matched tokens: cpp, version
- `arbor/morph/morphology.cpp` | score: 10 | matched tokens: cpp, morphology
- `arbor/communication/mpi_error.cpp` | score: 10 | matched tokens: communication, cpp
- `arbor/communication/mpi_context.cpp` | score: 10 | matched tokens: communication, cpp
- `arbor/communication/mpi.cpp` | score: 10 | matched tokens: communication, cpp
- `arbor/communication/dry_run_context.cpp` | score: 10 | matched tokens: communication, cpp
- `arbor/communication/communicator.cpp` | score: 10 | matched tokens: communication, cpp
- `python/units.cpp` | score: 7 | matched tokens: cpp, unit
- `python/single_cell_model.cpp` | score: 5 | matched tokens: cpp
- `python/simulation.cpp` | score: 5 | matched tokens: cpp
- `python/domain_decomposition.cpp` | score: 5 | matched tokens: cpp
- `python/schedule.cpp` | score: 5 | matched tokens: cpp
- `python/remote.cpp` | score: 5 | matched tokens: cpp
- `python/recipe.cpp` | score: 5 | matched tokens: cpp
- `python/pyarb.cpp` | score: 5 | matched tokens: cpp
- `python/profiler.cpp` | score: 5 | matched tokens: cpp
- `python/probes.cpp` | score: 5 | matched tokens: cpp
- `python/network.cpp` | score: 5 | matched tokens: cpp
