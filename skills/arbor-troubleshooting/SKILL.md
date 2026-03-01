---
name: arbor-troubleshooting
description: This skill should be used when users ask about troubleshooting in arbor; it prioritizes documentation references and then source inspection only for unresolved details.
---

# arbor: Troubleshooting

## High-Signal Playbook
### Route conditions
- Use this skill for reproducible error signatures in build/runtime/test flows.
- Route to `arbor-build-and-install` for first-time setup without a concrete failure yet.
- Route to `arbor-parallel-hpc` when the failure is specifically rank/GPU placement/scaling related.

### Minimal command/input
```bash
# Capture environment and run failing target with full output
python -c "import arbor as A; A.print_config()"
ctest --test-dir build --output-on-failure
```

### Validation checkpoints
- Failure is reproduced from a minimal command with full stderr/stdout captured.
- Build/runtime capability report (`A.print_config()`) is attached to the issue context.
- After a fix, re-run the same failing command plus one nearby regression test.

## Scope
- Handle questions about known issues, diagnostics, and debugging patterns.
- Keep responses abstract and architectural for large codebases; avoid exhaustive per-function documentation unless requested.

## Primary documentation references
- `doc/dev/debug.rst`
- `doc/contrib/issue.rst`

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
- `python/error.hpp`
- `python/error.cpp`
- `modcc/error.hpp`
- `arborio/debug.cpp`
- `arbor/communication/mpi_error.cpp`
- `arborio/include/arborio/debug.hpp`
- `arbor/include/arbor/communication/mpi_error.hpp`
- `modcc/errorvisitor.hpp`
- Prefer targeted source search (for example: `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`).
