# arbor source map: Cpp

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
- `adex`
- `cable`
- `cell`
- `cpp`
- `domdec`
- `event`
- `format`
- `generators`
- `interconnectivity`
- `labels`
- `lif`
- `mechanisms`
- `remote`
- `spike`

## Fast source navigation
- `rg -n "<symbol_or_keyword>" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- `rg -n "class|def|struct|namespace" arbor arborenv arborio lmorpho mechanisms modcc python sup`
- If a doc mentions a function/class, search that exact symbol first, then inspect nearby implementation files.

## Suggested source entry points
- `python/cable_cell_io.cpp` | score: 15 | matched tokens: cable, cell, cpp
- `arbor/spike_source_cell_group.cpp` | score: 15 | matched tokens: cell, cpp, spike
- `arbor/spike_event_io.cpp` | score: 15 | matched tokens: cpp, event, spike
- `arbor/lif_cell_group.cpp` | score: 15 | matched tokens: cell, cpp, lif
- `arbor/cable_cell_param.cpp` | score: 15 | matched tokens: cable, cell, cpp
- `arbor/cable_cell_group.cpp` | score: 15 | matched tokens: cable, cell, cpp
- `arbor/cable_cell.cpp` | score: 15 | matched tokens: cable, cell, cpp
- `arbor/adex_cell_group.cpp` | score: 15 | matched tokens: adex, cell, cpp
- `python/single_cell_model.cpp` | score: 10 | matched tokens: cell, cpp
- `python/remote.cpp` | score: 10 | matched tokens: cpp, remote
- `python/event_generator.cpp` | score: 10 | matched tokens: cpp, event
- `arbor/spike_source_cell_group.hpp` | score: 10 | matched tokens: cell, spike
- `arbor/thread_private_spike_store.cpp` | score: 10 | matched tokens: cpp, spike
- `arbor/lif_cell_group.hpp` | score: 10 | matched tokens: cell, lif
- `arbor/fvm_lowered_cell_impl.cpp` | score: 10 | matched tokens: cell, cpp
- `arbor/cell_group_factory.cpp` | score: 10 | matched tokens: cell, cpp
- `arbor/cable_cell_group.hpp` | score: 10 | matched tokens: cable, cell
- `arbor/benchmark_cell_group.cpp` | score: 10 | matched tokens: cell, cpp
- `arbor/adex_cell_group.hpp` | score: 10 | matched tokens: adex, cell
- `arbor/include/arbor/spike_source_cell.hpp` | score: 10 | matched tokens: cell, spike
- `arbor/include/arbor/spike_event.hpp` | score: 10 | matched tokens: event, spike
- `arbor/include/arbor/lif_cell.hpp` | score: 10 | matched tokens: cell, lif
- `arbor/include/arbor/cable_cell_param.hpp` | score: 10 | matched tokens: cable, cell
- `arbor/include/arbor/cable_cell.hpp` | score: 10 | matched tokens: cable, cell
- `arbor/include/arbor/adex_cell.hpp` | score: 10 | matched tokens: adex, cell
- `python/cells.cpp` | score: 7 | matched tokens: cell, cpp
- `arborio/cableio.cpp` | score: 7 | matched tokens: cable, cpp
- `arbor/merge_events.cpp` | score: 7 | matched tokens: cpp, event
- `arbor/domdecexcept.cpp` | score: 7 | matched tokens: cpp, domdec
- `python/simulation.cpp` | score: 5 | matched tokens: cpp
