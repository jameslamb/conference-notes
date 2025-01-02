# SciPy 2023

## Day 1

### A. Keynote - Open Source Maintainers in time and space

- metcalfe's law: "the value of a network is proportional to the square of its nodes"
- speaker: "the COST of a network is proportional to the squarer of the EDGES"
- "becoming an open source contributor is a privilege"
- advocated for synchronous meetups between maintainers and contributors, to "find out why people are contributing"

### B. SciPy Tools Plenary

- scikit-learn
    - learning curve display
    - partial dependence plots (that also supports categoricals)
    - HistGradientBoosting* now supports interaction constraints
    - `.set_output("pandas")`
- tiled
    - "structured data access service for SciPy-like data structures"
    - github.com/bluesky/tiled
    - "from HTTP straight into `numpy`"
- zarr
    - github.com/zarr-developers/community
- scikit-build
    - "CMake-based Python build-system from KiteWare, the makers of CMake"
    - `CMake` now ships Windows ARM wheels
    - `moderncmakedomain` (document CMake code in Sphinx)
- numba
    - `numba++` compiler
    - github.com/numba/pixie - a way to stick things into a library do do JIT compilation very fast
- scikit-image
    - added more structure around units of measure
    - `scikit-iimage` is making API changes in a new namespace

### C. Out-Performing NumPy is Hard: When and How to Try with Your Own C-Extensions

- speaker: Christopher Ariza
- why Python is slow
    - values are "boxed" in C `PyObjects`
    - values not in contiugous memory
    - have to keep track of reference counts
- a lot of `numpy` routines are "excessively flexible"
    - handle non-array (liist, tuple) inputs
    - handle n-diimensional arrays
    - handle full
- improving performance
    - numba
    - C extension
    - PY03
- "just putting it in C doesn't make it go faster"
- SIMD = "single instructiion, multiple data instructions"
    - AVX-512
- SIMD as "truue vectorization"
- https://static-frame.dev

### D. Can there be too much parallelism?

- speaker: Thomas J. Fan
- slides at github.comm/thomasjpfan/scipy-2023-too-parallel
- "you inherit the semantics of paralllelism from your dependencies", e.g. in scikit-learn...
    - BLAS through SciPy
    - OpenMP + Cython
    - Python multi-threading
    - Python multi-processing
- environment variables:
    - OMP_NUMM_THREADS
    - MKL_NUM_THREADS
    - OPENBLAS_NUM_THREADS
- configuration (Python functions)
    - `torch.set_num_threads()`
    - `numba.set_num_threads()`
    - `threadpoolctl`
- "a good future": `OMP_NUM_THREADS`
- `threadpoolctl` is just one file
- "consistent APIs is a social issue"
- oversubscription:
    - Ray, Dask recommend setting all the env vars to 1 to let them manage the parallelism
- "by default, scikit-learn uses `threadpoolctl` to control the number of threads in the inner loop"
- some parallel abstractions just don't work well together
    - Python multiprocessing with `fork` + GCC's version of OpenMP
    - Inntel OpenMP + LLVM OpenMP on Linux
    - https://github.com/thomasjpfan/parallelism-python-libraries-design
- for `conda-forge` packages, all packages share the same thread pool
    - so installing from `conda-forge` can actually make your stuff faster
- `intel-openmp` wheels are available on PyPI
- scikit-learn is already testing against Meta's nogil version of Python
- "it's technically possible to publish a conda package that only sets environment variables"
    - wut

### E. Disciplined Saddle Programming

- speaker: philipp schiele
- `cxvpy` is a thing for convex optimization problems
    - which are like "minimize a function relative to some constraints"
- `cvxpy.Problem(cp.Minimize(objective), constraints)`

### F.

- speaker: ammanda casari
- Google Open Souurce "Acknowledgment of Country"
    - the speaker started by reading out information about the native american groups whose land the space was built on
- "the indomitable state of vermont"
- bit.ly/breaking-the-internet
- "people from vulnerable populations may intentionally separate their identities across multiple spaces"
- how can you tie all open source contributions made by one physically person to one identity, when...
    - they use different aliases (e.g. company-specific accounts)
    - they come out as trans and cannot change commits tied to their dead name
- can foundations "opt-in" communiitiies and projects into ecosystem-scale research?
- books:
    - "Beyond the Repository: Best practices for open source ecosystems researchers"
    - "Data Feminisim" - Catherine D'Ignazio and Lauren F. Klein
    - "Forge Your Future with Open Source"
- bit.ly/oss-dragons-scipy2023-slides
- PyPI was subpoeana'd: https://blog.pypi.org/posts/2023-05-24-pypi-was-subpoenaed/
- there's a difference between data that exists and data you created

### G. In-process something something with DuckDB

- speaker: Alex Monahan
- DuckDB is "in-process", not "in-memory" (it can spill to disk)
- DuckDB is about bringing databases into workloads where dataframes have been more popular
- DuckDB is named after Hannes' pet duck
    - he lives on a house boat in Amsterdam
    - "we're not super-mega-awesomeDB, we want to be approachable"
- SQLite is a row-oriented database
- DuckDB end-to-end query optimization
    - looks ahead when planning your queries
- DuckDB has parallel versions of most operators, without you needing to specify any partitions
- he said "welcome to the flock" :joy:
- DuckDB is adding Iceberg support iin the next release

### H. GraphBLAS for Sparse Data and Graphs

- speakers: Jim Kitchen (Anaconda) and Erik Wlech (NVIDIA)
- graphs can be represented as sparse arrays
- with sparse data, most of the computation ends up just being 0 times 0
- "sparse linear algebra"
- SSSP (single-source-shortest-path)
- `python-graphblas`

### I. Lightning talks - PyVista

- PyVista = 3D visualization toolkit built on VTK
- create a "mmesh surface"

### J. Lightning Talks - Dask

- Dask expressions capture user intent
- dask-contrib/dask-expre
- TL;DR you throw a `.optimize()` on the end of your graph before running

### K. PyData Sphinx theme

- https://pydata-sphinx-theme.readthedocs.io/en/stable/
- pymeilisearch... Python wrapper on https://github.com/meilisearch/meilisearch

### J. Automating the Calibration of 8 TB of Data Per Day

- Inouye Solar telescope
- this talk was about using Apache Airflow to move 8TB of dataa per day from this telescope in Hawai'i to a data center in boulder
- "typically solar physics was done in IDL... we chose Python"
- "you are contributors to calibrating the largest solar dataset in the world"
- dkist.data.nso.edu - solar data

### K. Oscilloscopes: ADCs and Intrigue

### L. Lightning Talks - What Do SCientists Draw When they Draw Data?

- Sam Walkow

### M. Lightninng Talks - xarray

- rechunker: rechunking arrays using `zarr`
- and another project called `cubed`
    - https://github.com/tomwhite/cubed
- "coiled function service"

## Day 2

### A. Keynote

- insitro
- https://github.com/insitro/redun
- "scientific workflow and data provenance engine"
- https://insitro.medium.com/when-data-science-goes-with-the-flow-insitro-introduces-redun-8b06b707a14b
- NeurIPS

### B. Tools Plenary

- hypothesis
    - Cheuk Ting Ho
    - improvuded support for nummpy, pandas, array-api
    - "coverage-guided fuzzing"
- CPython 3.11
    - TOML support
    - fine-grained traceback locations
    - exception groups and notes
    - per-interpreter GIL (you can launch multiple interpreters in the same process)
- dask
    - significant immprovements in integration with Arrow (especially for string data)
- cibuildwheel
    - "simple enough for small projects, powerful enough for large projects"
- conda forge
    - 11bn downloads since March 2017
    - https://conda.org/blog/2023-07-05-conda-libmamba-solver-rollout/
    - Rust-based conda tooling
        - prefix-dev/pixi
        - mamba-org/rattler
- awkward array
    - interoperable with JAX
    - to/from CuPy arrays
- cython
    - Cython 3.0 is coming!

### C. Subpoenas Less Scary

- speakers: Rebecca BurWei, Dave Zeber (data scientists at Mozilla)
- some lawyer or whatever comes to your company and says "give us this data on your users..." and that eventually turns into work for a data team! writing SQL, pulling data into files, etc.
- "how we protect sensitive data"
    - clear access and retention policies
    - prevent joining (e.g. no user IDs associated with other data if not necessary)
    - no user profiles
    - remove PII
- a machine learning system can be a good fit for filtering PII
- simple PII filtering:
    - queries containing '@'
    - anything containing numeral 0-9
    - SpaCy has a named entity recognition (NER) model you can use to detect names
- "risk exposure" - "who is most at risk for privacy violation?"
    - e.g. "if you identify as Black, then your surname is 40% more likely to appear in the search queries dataset"
    - U.S. Census Bureau publishes a list of surnams by race
    - you see that the black surnames have a much tighter distribution... no "long right tail" like the white surnames

### D. jupyter-scatter

- scatterplots on a ton of data, interactive, zooming, v cool

### E. Using Python to accelerate sustainable aviation fuel research and development

- speaker: Ana Comasena
- FTIR spectra
- using machine learning to map molecular structure characteristics to performance characteristics,, to try to guide the development and testing of fuels for aviation
- things being predicted:
    - boiling point
    - viscosity
- "non-negative mmatrix factorization" = decopmoses data into "explanatory variables" and "expansion coefficients"

### F. Maintenance and Evolution of Zarr

- Josh Moore, Sanket Verma
- `@joshmoore@fediscience.org`
- zarr.dev/zeps

### G. MetPy

- "when one developer died, the only way we happened to get into a PyPI account was because we found a plaintext password in someone's home folder"
- speaker: Ryan May

### H. Lightning Talks - it doesn't work on my machine

- https://containers.dev
- there are mcr Microsoft miniconda docker iimages
- if you add a .devcontainer, you can get a little codespaces instance for free (???)

### I. Lightning Talks - pyscript

- WASM
- MicroPython

### J. Lightning Talks - numFOCUS academic consortium & open source pledge

- Arliss Collins

### K. Lightning Talks - Obfuscatinng Python Code

- deliberately complicating code so it works the same but so that no one can understand it
- `pyarmor` = obfuscated scripts

### L. Lightning Talks - How Government Policy can affect open-source

- speaker: cheuk ting ho

### M. Lightning Talks - Coiled

- speaker: James B from Coiled

### N. Lightning Talks - scikit-learn pandas out

- thomas fan
- yay dataframes

## Day 3

### A. tools - numpy

- new MUSL wheels
- no more need for the `oldest-supported-numpy` namespace
- "developer in residence" role
- there will be a 2.0 release in December / January!!
- they explicitly said "please put a version ceiling of `<2.0` in requirements"
- `numpy` is switching their build system to Meson

### B. tools - Ibis

- "SQL is difficult, but once you learn more about it it's even worse"
- github.com/ibis-project/ibis

### C. new CUDA toolkits on conda

- CUDA is a programming language, CUDA toolkit is a bundle of stuff like a compiler (NVCC), debugger (cuda-gdb), various libraries
- "two conda packages can share their dynamic libraries"
- there are `nvidia`, `rapidsai`, `numba`, `dask`, `pytorch` conda channels
- there's a `__cuda` mmeta package on conda to detect the version of CUDA installed
    - in your recipe, you just provide `{{ compiler("cuda") }}` in `requirements/build` in your recipe
    - you still have to install CUDA yourself
    - "if it's not broke, iit doesn't have enough features"
- image tracking restructuring of the cuda toollkit into smaller packages: https://github.com/conda-forge/cudatoolkit-feedstock/issues/62
    - learned from that that you can do this: `mamba repoquery depends -q -c conda-forge --tree catboost`

### D. Array API stuff

- `__array_function__dispatching`
- "there's more to an array API than just function signatures"
    - indexing?
    - type promotion?
- `scipy` and `scikit-learn` are both moving to adopt the array API
- change `import numpy as np` to `xp = array_namespace(x)`
- so you can just pass in any array supporting this and the library dispatches appropriately
- the spec has a strong preference for functions, over mmethods
- github.com/data-apis/array-api-compat
- `numpy.array_api` is a strict minimal implementation of the standard

### E. What to do when the main maintainer steps down

- porkchop plots
- `poliastro`
- Libre polaris
- add a `contrib/` directory and make that the newcomer-friendly zone
- give talks to get people interested

### F. DataJoint

- DataJoint
    - defining computational dependencies
    - querying
    - data lineage
- this is some kind of workflow management thing
- they made a little thing where you create basically ORM objects, but then construct queries using overridden magicm ethods and operators

### G. from espaloma to SAKE: to brew, distill, and miix force fields with balanced briskness, smmoothness, and intricacy

-

## Things to Google / Read

- Aerospike (database)
- "anti-aliasing"
- chatGPT article: https://www.wired.com/story/chatgpt-jailbreak-generative-ai-hacking/
- "consortium for Python data API standards"
    - https://data-apis.org/
- CPython "dead batteries" PEP
- dev containers (https://containers.dev)
- diiataxis framework (for docs)
- einops
- free motion capture thing: https://github.com/freemocap/freemocap
- gamma loss (for modelling waiting times)
- IIbiis
- "inlined comprehensions" PEP: https://peps.python.org/pep-0709/
- JupySQLL
- libmamba becoming the default: https://conda.org/blog/2023-07-05-conda-libmamba-solver-rollout/
- meilisearch
- MicroPython
- Mojo
- "the mythical man-month" (book)
- OpenBLAS issue (https://github.com/xianyi/OpenBLAS/issues/3187)
- openLayers
- Project Ocean (mapping out open source contribution)
- pyscript.com
- `pyspy` (profiling): https://github.com/benfred/py-spy
- Python parallelism design (https://github.com/thomasjpfan/parallelism-python-libraries-design)
- "Securing Open Source Software Act"
- siuba
- sli.dev (thing for making slides)
- staticframe (https://github.com/static-frame/static-frame)
- tiled (github.com/bluesky/tiled)
- zarr
- zulip (open source chat app)
