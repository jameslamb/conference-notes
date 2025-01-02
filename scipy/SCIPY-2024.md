# SciPy 2024

schedule: https://www.scipy2024.scipy.org/schedule

## Day 1

### A. Keynote - The Right Tool for the Job

* speaker: Julia Silge
* costs of using multiple languages:
    - who can do code review?
* "I know some people who have been writing one programming language their whole careers and are happy... but that's really rare"
* gave the example of when you learn another (human) language, and you sometimes learn a word that just perfectly expresses some concept
    - the same can be true for programming languages... learning another one can expose you to different ways of thinking, different concepts that are just perfectly expressed in one language and difficult to express in another
* example
    - roxygen is directly inspired by doxygen
    - R does not have built-in interpolated string literals... but people built `{glue}`
* "if you're just starting your career, learn one programming language well... become a baddie in one thing"
* pitched https://github.com/posit-dev/positron

### B. Tools Plenary

* `scikit-image` is looking for a new logo based on their import name (`skimage`, "ski" and "mage")
* `scipy`
    - enabled "Apple's Accelerate BLAS/LAPACK"
    - new "random variable infrastructure"
* Journal of Open Source Software - passed 2500+ papers
* Ibis
    - "we stopped using Postgres' awful practice of having 'schema' mean 3 different things"
    - "you can use DuckDB and Ibis and PyArrow
    - "Zulip is like Slack but your data isn't held by a random VC"
    - this was a great talk :joy:

### C. Python for early-stage design of sustainable aviation fuels

* speaker: Ali Martz
* using Bayesian Optimization to explore the search space of chemical "recipes" for jet fuels

### D. Monte Carlo/Dynamic Code: Performant and Portable High-Performance Computing at Scale via Python and Numba

* speakers: Joanna Piper Morgan, Kyle Niemeyer
* "the Monte Carlo method was invented as part of the Manhattan project"
* "performance portability frameworks":
    - Kokkos / Raja
    - DSLs + Python Glue
    - Julia
    - Numba
* "Numba is a wrapper for LLVM ... it's sort of a subset of Python"
* "on CPUs, we use `mpi4py` to do distributed-memory parallelism"
* this was fascinating and so clarifying:
    - OpenMP as "shared-memory parallelism"
    - MPI as "distributed-memory parallelism"
* MC/DC: https://github.com/CEMeNT-PSAAP/MCDC
* "on GPUs, we can't ensure everything will execute serially within a thread"
    - "e.g. for an array addition, we have to be sure we're doing an atomic add"
* they saw 21-24x speedup on 1 Tesla V100 (compared to an Intel Xeon E5-3695 CPU)
* "Limitations of Numba"
    - Unsupported C-side functions (MPI, memalloc)
    - Undocumented IR generation behavior
    - Long compile times
    - Lacking ahead-of-time compilation
    - Lack of compiled kernel profiling on CPUs or GPUs
    - Cryptic compiler errors
* they're trying to add AMD GPUs
* purpose: "Advancing the state of the art of Monte Carlo neutronics calculations particularly for solving time-dependent transport problems on exascale computer architectures in a sustainable open-source community"
* "performance portability frameworks, specifically `numba`, has allowed us to make a ton of progress"
* this was an AWESOME talk... packed room, standing-room only

### E. How to foster an open source culture within your data science team

* speaker: Eric Ma (Moderna)
* "import open source ways of working"
* "one-off analyses have less guarantees of sustained impact compared to composable and reusable tools"
* "in open-source world, you cannot get away with sloppy, untested code"
* "documentation scales brains"

### F. My NumPy year: From no CPython C API experience to shipping a new DType in NumPy 2.0

* speaker: Nathan Goldbaum
* great talk, really funny
* using the `numpy` `object` dtype by default for string arrays is "ecosystem-wide technical debt"
    - an `object` array holds references to Python objects
* if `numpy` had had better string support by default it might have avoided `pandas` having `object` columns and all the pain that led to (including PDEP-10 and all the agita around `pyarrow` being a hard dependency)
* for a large project, it's useful to work in a place that's public, but not as noisy as the main repo
* "usually, then number one thing blocking a project is lack of code review"
* "eventually, your inability to merge code will cause inefficiency and eventually you'll get a commit bit"
* I (james, me) asked if this work had any side effects on `blosc` or the `.npy` file format... speaker said that this actually could not be added to the `.npy` file because of the array-of-pointers approach (it'd require a major version bump to `.npy`)
* "if you run the `pandas` test suite on a single core with no parallelization it takes like a day"

### G. Coming Online: Enabling Real-Time and AI-Ready Scientific Discovery

* speaker: Adam Thompson
* "traditionally GPUs are high-bandwidth, but also high-latency"
* talked about NVIDIA "Holoscan"
* "data movement is abstracted away with UCX"
    - UCX will understand whether you have nvlink or RDMA or whatever other interconnect

### H. Sparse arrays in scipy.sparse

* speaker: Dan Schult
* `scipy.sparse` matrix things are deprecated and will be removed in a few releases... time to start switching
* migration:
    - add support for `scipy.sparse` ARRAYS
    - replace `isspmatrix_csr(X)` (and similar) with like `is_sparse(X) and X.format == "csr"`

### G. No-Code-Change GPU Acceleration for Your Pandas and NetworkX Workflows

* speakers: rick ratzel, vyas ramasubramanian

whoa

```python
G = nx.from_pandas_edgelist(
    edgelist_df,
    source="src",
    target="dst",
    create_using=nx.DiGraph,
    backend="cugraph"
)
```

### H. Lightning talks

* `conda-store` = reproducible conda environments (demo'd with nebari)
* `nvmath-python` (Segey Maydanov)
* checkout out reactive functions in `panel` / `holoviz`
    - gave the example of an expression in a Jupyter cell dependent on a slider

## Day 2

### A. Keynote

* "just refer to deep learning as 'non-linear regression' and people will relax"

### B. tools plenary

* `nextworkx` alternative backgrounds:
    - `nx-parallel` (to use joblib)
    - `nx-cuGraph` (to use GPU based algorithms)
    - `graphblas-algorithms` (for GraphBLAS implementations)

### C. New Developments in Open Source Computational Economics

* "a lot of economics work is being done in Julia now"
* "you can go straight from SymPy to JAX now"

### D. NumPy 2.0 BoF

* build-related stuff (`meson-build`) was a problem for some folks

### E. When is Rust beneficial for Data Scientists?

* speaker: Akshay Gupta
* this talk is about re-writing stuff :sparkles: in rust :sparkles:
* `polars` has a plugin system
* "given enough eyeballs, all bugs are shallow"
    - writing something that few people will understand is risky because it means few people will read it and therefore find bugs

### F. Building Daft: Python + Rust = a better distributed query engine

* speaker: Jay Chia
* Daft can be scaled up to be distributed via `ray`
* multimodal data: Daft supports columns of images :whoa:
* things to look into:
    - `[pyfunction]`
    - `py.allow_threads()` = drop the GIL from a Python thread
* great talk!

### G. Introducing nanoarrow: the world's tiniest Arrow Implementation

* speaker: Dewey Dunningham (Voltron data)
* `cudf` got a great shout-out! "it's one of the coolest things I've participated in"
* data-sharing protocols
    - `PyBuffer`
    - `DLPack` (specific to the GPU)
    - `DataFrame`
    - `Arrow`
* `cudf` was highlighted 2 different times in this talk
* "distributing a package with a `pyarrow` dependency is pretty difficult"
    - there is a `nanoarrow-python`: https://arrow.apache.org/nanoarrow/latest/getting-started/python.html

### H. Dante’s Externo: Injecting Python Functions into a Template-Driven CUDA C++ Framework

* speaker: Braxton Cuneo
* follow-up to MC/DC test from Day 1
* "GPUs rely on single-instruction-multiple-thread (SIMT) processing"
* GPUs favor:
    - threads within the same warp taking the same paths in a program
    - higher data locality
* making more things async was key to being able to run on GPU and CPU
* "the ffi sandwich"
* great speaker
* "PTX isn't linkable"
    - so you have to generate object files with RDC (relocatable device code) and PIC (position-independent code)
    - `nvcc -dlink`
* "object mode" (in the context of "the CUDA array interface")
    - https://numba.pydata.org/numba-doc/latest/glossary.html#term-object-mode
* this talk had lots of critical feedback for numba, I'd almost say it was "delivered in anger". Really liked it1

### I. Lightning Talks

* `swiftascmaps` (color maps based on Taylor Swift album covers)
* MyST
* `renovate` talk said that the project is great and maintainers respond really quickly to questions

## Day 3

### A. Scikit-build-core: A modern build-backend for CPython C/C++/Fortran/Cython extensions. SciPy 2024

* speaker: jean-christophe fillion-robin
* `scikit-build` was released as PyCMAKe at SciPy 2014
* oh you can use `scikit-build-core` and `pybind11` together

```toml
[build-system]
requires = ["scikit-build-core", "pybind11"]
build-backend = "scikit_build_core.build"
```

* PEP 517 allows the build backend to dynamically update the build dependencies
* features:
    - `site-packages` added to CMake search path
* default editable mode: detect changes, copy files into build tree
* in-place mode: similar to `setup.py build_ext --inplace`
* you can generate files!

```toml
[[tool.scikit-build.overrides]]
```

### B. Ibis: because SQL is everywhere and so is Python

* speaker: Gil Forsyth
* GREAT talk
* "the interface and the engine (for dataframe parsing) are not the same"
* "Ibis provides a Pythonic dataframe interface to 20+ engines"
* SQL had different dialects, so saying the interface is SQL is hiding a lot of stuff
* "SQL has a standard, but it ain't standard"
* Ibis uses `sqlglot` heavily, as part of its `compile()` step

### C. ITK-Wasm: Universal spatial analysis and visualization

* speaker: matt mccormick (Kitware)
* WASM
    - a virtual binary instruction set for a simple, abstract stack-based machine
    - runs in secure sandbox
    - portable
    - fast
* these features tend to make WebAssembly stuff highly sustainable (it should run for years)
* emscripten is a toolchain for compiling C/C++ stuff to WASM
    - example: `pyodide`
* ITK-Wasm enables spatial scientific C/C++ code usage via Wasm

### D. Lightning talks

* there was a talk where they piped the video camera to ChatGPT to generate text in the way David Attenboro (the Planet Earth narrarator) would talk, and then that text to a voice-generator thing, and playt it out loud
* how to use GPUs on CI/CD
    - see conda-forge `open-gpu-server` (Quansight)
    - ubicloud-gpu
    - get a T4 GitHub Actions runner from NVIDIA

## Things to Google / Read

* abandoned.ai
* Accelerate BLAS/LAPACK (Apple)
* Another Open Source Podcast - "Parents of Open Source"
* arm runners from ubicloud:
    - https://www.ubicloud.com/blog/ubicloud-hosted-arm-runners-100x-better-price-performance
* CMake's "File API"
* "Getting to Yes" (book)
* github.com/apache/arrow-nanoarrow
* "unicode sandwich" (`astropy`)
* BoTorch (bayesian optimization)
* `cuda.declare_device()` (in `numba`)
* DataTree (`xarray`)
* `dockcross` (https://github.com/dockcross/dockcross)
* ECON-Ark
* `einops` (https://einops.rocks/)
* Great Tables (Posit)
* Harmonize (templating)
* IbisML (`ibis-ml`)
    - claimed XGBoost support
* Kokkos / Raja
* `marimo` (notebooks)
* MyST (https://myst-parser.readthedocs.io/en/latest/)
* Numba `@njit`
* NumPy 2.0 DType API
* `pins` (Posit)
    - https://pins.rstudio.com/
* `polars` & `polars` plugin system
* RisingWave
* `scikit-learn-intelex` (Intel(R) extension for scikit-learn)
* WebAssembly System Interface (WASI)
* `vetiver` (Posit)
* xarray `NamedArray`
