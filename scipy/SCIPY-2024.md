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

## Things to Google / Read

* Accelerate BLAS/LAPACK (Apple)
* "unincode sandwich" (`astropy`)
* BoTorch (bayesian optimization)
* DataTree (`xarray`)
* Great Tables (Posit)
* Harmonize (templating)
* IbisML (`ibis-ml`)
    - claimed XGBoost support
* Kokkos / Raja
* Numba `@njit`
* NumPy 2.0 DType API
* `pins` (Posit)
    - https://pins.rstudio.com/
* `polars`
* RisingWave
* `vetiver` (Posit)
* xarray `NamedArray`
