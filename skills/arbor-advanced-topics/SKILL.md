---
name: arbor-advanced-topics
description: This skill consolidates low-signal one-doc Arbor topics (general overview, release procedure, requirements, validation data notes, and developer-guide index) into one docs-first router.
---

# arbor: Advanced Topics

## Scope
- Consolidated router for narrow one-doc topics that are still useful but too fragmented as standalone skills.
- Use for package-level metadata/process docs, release workflow, requirements listing, and validation data organization.

## Route the request
- Release workflow, version tagging, PyPI/TestPyPI process: use `doc/contrib/release.rst`.
- High-level developer doc entry point and internal toctree: use `doc/dev/index.rst`.
- Global package/documentation orientation: use `doc/index.rst`.
- Documentation build requirements package list: use `doc/requirements.txt`.
- Validation data directory layout and generation target: use `validation/README.md`.
- If the user’s question becomes operational (build flags/runtime/debugging), route to `arbor-build-and-install`, `arbor-parallel-hpc`, or `arbor-troubleshooting`.

## High-Signal Playbook
### Minimal command/input
```bash
# Quick environment sanity check before release/validation guidance
python -c "import arbor as A; A.print_config()"
```

### Validation checkpoints
- Printed config matches expected MPI/GPU/vectorization capabilities for the target environment.
- `validation/README.md` guidance and `validation/CMakeLists.txt` targets agree before recommending data-generation steps.
- If this becomes a concrete runtime/build failure, route with the exact command/error to `arbor-troubleshooting`.

## Primary documentation references
- `doc/index.rst`
- `doc/dev/index.rst`
- `doc/contrib/release.rst`
- `doc/requirements.txt`
- `validation/README.md`

## Workflow
- Start from the exact reference above matching user intent.
- If more detail is needed, jump to linked subordinate docs from that page's toctree/headings.
- Escalate to source only for behavior details not covered in docs/process text.

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
- `validation/CMakeLists.txt`
- `test/CMakeLists.txt`
- `arbor/version.cpp`
- `arbor/util/config.hpp`
- `arborenv/read_envvar.cpp`
- `python/env.cpp`
- `python/error.cpp`
- `arborio/debug.cpp`
- `modcc/errorvisitor.cpp`
- `modcc/error.hpp`
- `scripts/create_tarball`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
