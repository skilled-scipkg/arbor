# arbor documentation map: Build and Install

Generated from documentation roots:
- `doc`
- `example`
- `python/example`
- `test`
- `validation`
- `python/test`

Total docs grouped in this topic: 44

## File inventory
- `test/ubench/README.md` | title: Library microbenchmarks | headings: Library microbenchmarks; Building and running; Adding new benchmarks
- `example/generators/readme.md` | title: Event Generator Example | headings: Event Generator Example; The Recipe; Describing The Network
- `doc/install/index.rst` | title: Get Arbor | headings: Get Arbor
- `validation/CMakeLists.txt` | title: Validation data generation | headings: Validation data generation; Helper function because ffs CMake.; Helper function to add a data generation script that writes to standard output.
- `test/CMakeLists.txt` | title: Convenience target that builds all tests. | headings: Convenience target that builds all tests.; Test executable targets should be added to the 'tests' target as dependencies.; Unit tests.
- `doc/install/build_install.rst` | title: ... | headings: ...; Build and install from source; Getting the code
- `doc/cpp/morphology.rst` | title: Cable cell morphology | headings: Cable cell morphology; Segment tree; Morphology API
- `doc/contrib/code.rst` | title: Install the formatter if not present | headings: Install the formatter if not present; Automatically apply style to all Python files. If unsure what this does read on.; Code
- `doc/dev/version.rst` | title: Version and build information | headings: Version and build information; Version information; Source information
- `doc/install/spack.rst` | title: Spack Installation | headings: Spack Installation; Install Arbor; Build Options
- `doc/install/python.rst` | title: Python Installation | headings: Python Installation; Getting Arbor; Customising Arbor
- `doc/dev/communication.rst` | title: Communication in Arbor | headings: Communication in Arbor; Exchange of Spikes; Distribution of Events to Targets
- `doc/contrib/dependency-management.rst` | title: Dependency management | headings: Dependency management; List of dependencies; User platforms
- `example/CMakeLists.txt` | title: Convenience target that builds all examples. | headings: Convenience target that builds all examples.; Example executable targets should be added to the 'examples' target as dependencies.
- `doc/CMakeLists.txt` | title: Remove generated documentation when make clean is run. | headings: Remove generated documentation when make clean is run.
- `test/unit/CMakeLists.txt` | title: Build mechanisms used solely in unit tests. | headings: Build mechanisms used solely in unit tests.; Unit test sources
- `test/ubench/CMakeLists.txt` | title: List of micro benchmarks to build. | headings: List of micro benchmarks to build.; Build benches.
- `python/test/CMakeLists.txt` | title: Unit tests. | headings: Unit tests.; Builds: unit.
- `doc/install/gui.rst` | title: Arbor GUI | headings: Arbor GUI; Get Arbor GUI
- `doc/install/playground.rst` | title: Arbor Playground | headings: Arbor Playground
- `test/unit-modcc/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `test/unit-distributed/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/v_clamp/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/single/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/ring/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/remote/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/probe-demo/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/plasticity/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/ornstein_uhlenbeck/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/network_description/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/lfp/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/generators/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/gap_junctions/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/dryrun/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/drybench/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/diffusion/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/busyring/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/busyring-tiled/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/brunel/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/bench/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `example/adex/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
- `validation/ref/numeric/CMakeLists.txt` | title: note: function add_validation_data defined in validation/CMakeLists.txt | headings: note: function add_validation_data defined in validation/CMakeLists.txt
- `validation/ref/neuron/CMakeLists.txt` | title: note: function add_validation_data defined in validation/CMakeLists.txt | headings: note: function add_validation_data defined in validation/CMakeLists.txt
- `python/test/cpp/CMakeLists.txt` | title: Cmakelists | headings: (no heading extracted)
