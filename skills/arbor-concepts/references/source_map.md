# arbor source map: Concepts

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
- `concepts`
- `discretization`
- `interconnectivity`
- `network`
- `domain decomposition`
- `cv policy`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- `rg -n "class|def|struct|namespace" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `arbor/include/arbor/simulation.hpp` | API contract for simulation semantics.
- `arbor/simulation.cpp` | Main simulation control flow used by concept docs.
- `arbor/include/arbor/domain_decomposition.hpp` | Domain decomposition interface and invariants.
- `arbor/domain_decomposition.cpp` | Domain decomposition implementation details.
- `arbor/partition_load_balance.cpp` | Core load-balancing behavior for interconnectivity setup.
- `arbor/include/arbor/network.hpp` | Network abstraction surfaced in concept-level discussions.
- `arbor/network.cpp` | Network construction and dispatch behavior.
- `arbor/network_impl.cpp` | Internal network execution behavior.
- `arbor/connection.hpp` | Connection representation used by interconnectivity.
- `arbor/spike_event_io.cpp` | Spike/event movement for connectivity semantics.
- `arbor/include/arbor/cv_policy.hpp` | CV policy API used by discretization docs.
- `arbor/cv_policy.cpp` | CV discretization behavior.
- `python/simulation.cpp` | Python mapping of simulation semantics.
- `python/network.cpp` | Python mapping of connectivity and network operations.
- `python/domain_decomposition.cpp` | Python mapping of decomposition behavior.
- `python/recipe.cpp` | Recipe behavior and method contracts used in concept-level patterns.
