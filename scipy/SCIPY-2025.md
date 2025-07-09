# SciPy 2025

schedule: https://www.scipy2025.scipy.org/schedule

## Day 1

### A. Keynote - 

### B. Python for Climate Science: Using Intake to provide easy access to Climate Model data

speaker: Charles Turner, ACCESS-NRI

* https://github.com/intake/intake
* "the pain is the pitch"
* "entrypoints aren't only for console scripts, you can also use them for plugins"
* "performance IS usability"
* "there are no stupid questions, just bad documentation"
* "training and support is as important as the tool itself"
* wonderful, entertaining speaker

### C. GBNet: XGboost and LightGBM PyTorch Modules

speaker: Michael Horrell

* "XGBoost / LightGBM / CatBoost need gradients... JAX, PyTorch, Tensorflow generate gradients"
* "mini-batching is kind of difficult"
* note

### D. Keynote

### E. EffVer

### F. Packagin a Scientific Python Package

* speaker: Henry Schreiner
* https://cfp.scipy.org/scipy2025/talk/RECJVV/
* `PYTHONSAFEPATH`: https://docs.python.org/3/using/cmdline.html#cmdoption-P
* `[dependency-groups]` in `pyproject.toml` are "developer dependencies"
* "`hatchling` is the recommendations for pure-Python"
* other backends:
    - `setuptools`
    - `pdm-backend`
    - `flit-core`
    - `poetry-core`
    - `uv-build`
    - `scikit-build-core`
    - `maturin`
* in addition to `__all__`, should define `__dir__()`
    - docs on this: https://learn.scientific-python.org/development/patterns/exports/
* look into `blacken-docs`:
    - https://github.com/adamchainz/blacken-docs
* use `ruff` `SCF` to check for deprecated `setuptools` stuff

### G. Scaling AI/ML Workflows on HPC for Geoscientific Applications.

speaker: Negin Sobhani

* URL: https://cfp.scipy.org/scipy2025/talk/8WQQPV/
* two bottlenecks:
    - data loading (PyTorch DDP)
    - model synchronization
* NCCL as "difficult to set up"
* AWS_OFI_NCCL plugin
    - uses `libfabric` (OFI) for higher-performance communications
    - AWS Elastic Fabric Adapter (EFA)
* "NCCL outperforms MPI and `gloo` for very large tensors, regardless of settings"
* "MPI can be used with or without GPU, and performs better than its counterparts for small tensors"
* "Communication between GPUs across nodes is significantly slower than within-node NVLink or PCIe"
* `zarr` v3 GPU support:
    - https://github.com/rapidsai/kvikio/pull/646
    - https://github.com/zarr-developers/zarr-python/pull/2863
* lots of RAPIDS stuff mentioned in this talk

### H. KvikUproot - Reading and Deserializing High Energy Physics Data with KvikIO and CuPy

speaker: Frank Strug

* URL: https://cfp.scipy.org/scipy2025/talk/RM3UHE/
* ROOT is a *collection* of file formats, including `TTree` and `RNTuple`
    - https://root.cern/doc/v622/md_tree_ntuple_v7_doc_README.html
* "no tools exist for efficiently streaming ROOT data from storage to GPU memory"
* GPUDirect storage = no need to create a "bounce buffer through the CPU" (i.e. loading data into system memory then copying into GPU memory)
* `kvikio` can be more efficient even if you don't have GDS
* found that for larger data sizes, `kvikio`'s POSIX API (ignoring GDS) actually had higher throughput than GDS
* expressed "we did lots of benchmarking, and despite that found it hard to figure out when to use GDS vs. POSIX API for `kvikio`"
* noted challenge: "`cupy` has gaps in coverage of `numpy` domain (like "structured arrays" and `np.insert()`)"
* mentioned that they're planning to switch to the `nvcomp` Python bindings, since those bindings were deprecated in `kvikio`
* "when you use GPUDirect Storage, the CPU is still driving that process"
* only certain filesystems and types of drives support GDS

## Things to Google / Read

* Argos catalogs
* AWS Elastic Fabric Adapter (EFA)
* COSIMA cookbook (for ocean - sea ice data): https://github.com/COSIMA/cosima-cookbook
* `cramjam` (https://github.com/milesgranger/cramjam): Python bindings for a bunch of compression / decompression algorithms
* diataxis (how to write good docs): https://diataxis.fr/
* Infiniband
* `libfabric`
* MPI: "CRAY MPICH vs. OpenMPI"
* new wheel types: Android wheels, iOS wheels, GraalPy wheels
* `numpy` "structured arrays": https://numpy.org/doc/stable/user/basics.rec.html
* Nsight / "NVTX markers"
* Python entrypoints: https://packaging.python.org/en/latest/specifications/entry-points/
