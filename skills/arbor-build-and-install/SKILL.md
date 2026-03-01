---
name: arbor-build-and-install
description: This skill should be used when users ask about build and install in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: Build and Install

## High-Signal Playbook
### Route conditions
- Use this skill for install strategy (`pip`, `spack`, or source/CMake), compiler/toolchain setup, and build-flag selection (`doc/install/index.rst`, `doc/install/build_install.rst`, `doc/install/python.rst`, `doc/install/spack.rst`).
- Route to `arbor-parallel-hpc` for rank/thread/GPU runtime placement or scaling diagnostics.
- Route to `arbor-troubleshooting` when there is already a concrete error signature from configure/build/test runtime.

### Triage questions
- Is the target interface Python-only, C++ library use, or both?
- Need MPI, GPU (`cuda`, `cuda-clang`, `hip`), vectorization, or a CPU-only build?
- Is this an offline package-manager flow (`spack`) or direct source build?
- Are `CC`/`CXX` pinned to a C++17-capable compiler (`doc/install/build_install.rst`)?
- Was the repo cloned with submodules (`--recurse-submodules`)?
- For Python+MPI, is `mpi4py` installed before building (`doc/install/python.rst`)?

### Canonical workflow
1. Pick install mode first: `pip`, `spack`, or source build (`doc/install/index.rst`).
2. Verify compiler and dependencies (`doc/install/build_install.rst`, `doc/dependencies.csv` referenced there).
3. Configure with minimal required flags only, then add MPI/GPU/vectorization flags (`doc/install/build_install.rst`, `doc/install/python.rst`).
4. Build core targets, then tests/examples (`doc/install/build_install.rst`, `example/readme.md`).
5. Run smoke checks (`./bin/unit`, Python import/config print).
6. Record exact CMake/pip args for reproducibility.

### Minimal working example
```bash
# Source/CMake flow (docs: doc/install/build_install.rst)
git clone https://github.com/arbor-sim/arbor.git --recurse-submodules
cd arbor && mkdir -p build && cd build
cmake .. -DARB_WITH_MPI=ON -DARB_GPU=none
make -j4 tests examples
./bin/unit
python -c "import arbor as A; A.print_config()"
```

```bash
# Python flow with compile flags (docs: doc/install/python.rst)
python -m venv arbor_env && source arbor_env/bin/activate
pip install mpi4py
CMAKE_ARGS="-DARB_WITH_MPI=ON -DARB_VECTORIZE=ON -DARB_ARCH=native" pip install ./arbor
python -c "import arbor as A; print(A.config())"
```

### Pitfalls and fixes
- Missing submodules causes configure warnings/errors: run `git submodule update --init --recursive` (`doc/install/build_install.rst`).
- Wrong default compiler selected by CMake: set `CC`/`CXX` explicitly before `cmake` (`doc/install/build_install.rst`).
- Python+MPI build fails to find mpi4py headers: install `mpi4py` before `pip install` (`doc/install/python.rst`).
- GPU requested but unsupported toolkit/toolchain: align `ARB_GPU` mode with installed CUDA/HIP toolchain (`doc/install/build_install.rst`, `doc/install/python.rst`).
- Aggressive vectorization/arch flags fail on target CPUs: start with `ARB_ARCH=native` and only then specialize (`doc/install/build_install.rst`).
- `spack install arbor` compiler resolution failure: run `spack compiler add` (`doc/install/spack.rst`).

### Convergence/validation checks
- `python -c "import arbor as A; print(A.config())"` shows expected MPI/GPU/vectorization flags (`doc/python/hardware.rst`).
- `./bin/unit` passes after configure/build (`doc/install/build_install.rst`).
- At least one shipped example builds and runs (`example/readme.md`, e.g. `bin/dryrun`).
- If using MPI/GPU, run one feature-specific smoke run and confirm no fallback to CPU-only behavior.

## Scope
- Handle questions about build, installation, compilation, and environment setup.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `test/ubench/README.md`
- `example/generators/readme.md`
- `doc/install/index.rst`
- `validation/CMakeLists.txt`
- `test/CMakeLists.txt`
- `doc/install/build_install.rst`
- `doc/cpp/morphology.rst`
- `doc/contrib/code.rst`
- `doc/dev/version.rst`
- `doc/install/spack.rst`
- `doc/install/python.rst`

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
- `CMakeLists.txt`
- `arbor/CMakeLists.txt`
- `arborenv/CMakeLists.txt`
- `arborio/CMakeLists.txt`
- `mechanisms/BuildModules.cmake`
- `modcc/CMakeLists.txt`
- `python/CMakeLists.txt`
- `arbor/version.cpp`
- `arbor/communication/mpi.cpp`
- `arborenv/private_gpu.cpp`
- `arborenv/default_env.cpp`
- `python/env.cpp`
- `arborio/nml_parse_morphology.cpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
