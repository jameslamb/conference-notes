# SciPy 2022

## Day 1

### A. Keynote - Software and Services to Fully Realize the Impact of AI, Machine Learning, Automation, and Community Engagement in Science

- speaker: Ben Blaiszik
- "materials genome initiative" = investment from governments to try to cut in half the time it takes to diiscover new materials
- given the earliest reports of COVID in Jan 2020, "an informal Slack with 300+ researchers from dozens of DOE labes an academic institutions was formed"
- funcx (www.funcx.org)
- globus
    - "data movement across distributed endpoints"
    - "build data portals"
- "the Moment platform"
    - "crediting micro research contributions"
    - "an open source collaboration platform"
    - goal oof mmaking it easier for people to make small, maybe software-only, contributions to ongoing scientific research
- this talk was pre-recorded, and had like 10+ guest speakers
- Argonne + DOE "self-driving iaboratories"
- getting involved --> github.com/blaiszik/scipy, twitter.com/BenBlaiszik
- with this work, they were analyzing data coming out of APS "in less time than it took to change a sample"

### B. Better Tests for Scientific Code

- speaker: Zac Hatfield-Dodds
- "property-based testing, Hypothesis, and the SciPy ecosystem"
- "we often ddon't know the correct results in scientific code, but we do have strong invaarriants and bounds on output"
- Hypothesis is a property-based testing project

### C. SciPy Build times

- `scipy` uses a CLI called `dev.py` for builds
- github.com/pydoit/pydevtool
- "completed privatizing naamespaces that were public but not intended to be"
- a collection of projects (`pandas`, `matplotlib`, `numpy`, `scipy`) have received $1M+ in grants
    - incl. NASA ROSES

### D. Astropy

- author: Matt Craigh
- most operations are done by just one or two people

### E. Awkward Array

- author: Jim Pivarski
- "awkward array"
- interoperability with JAX autodiff, CuPy
- a C++ header-only mode

### F. scikit-learn

- author: Thomas Fan
- coming in sciki-learn 1.1, `HistGradientBoostingClassifier` will support quantile regression
- "lots of improvements taking advantage of `scipy` and OpenMP"
    - upgrade and it "just runs faster"
- transformers and pipelines now support `get_feature_names_out()` to extract feature nammes

### G. Geospatial analysis and visualization with PyGMT

- GMT = "generic mapping tools"
    - 34-year-old technology for processing geospatial data and making maps
- PyGMT = Python package for GMT
- github.com/maxrjones/scipy2022
- PyGMT can be used with `geopandas` data frames
- you build up a `pygmt.Figure()` and then add layers to it
- `grd2xyz()` can be used to get a dataframe representation of a gridd
- github.com/GenericMappingTools/pygmt

### H. PyConf: A Framework for Reliable and Efficient Configuration of Complex Workflows

- speaker: niklas nolte
- https://gitlab.cern.ch/lhcb/Moore/tree/b207db1c8d08c0dc0f32e62d46efa46b0e63c4d1/PyConf/python/PyConf
- used by CERN
- "python compositions generate C++ code"
    - stuff will be JIT compiled on demand
- lots of data, little time -> need to be fast
- "having people just write C++ was something we (CERN) tried for 10+ years, and it was a mes"
- they basically wrote a thing where you describe data flow, data selections, etc. in Python and it coded-generates a pure-C++ application
- this is cool for lots of reasons, including that you can use PYTHON breakpoints (not `gdb`) to inspect state

### I. Pylira: deconvolution of images in the presence of Poisson noise

- speaker: axel donath
    - "a gamma ray andd x-ray astronomer, working at Harvard Smithsonian in Boston"
    - CHASC (Astro-Statistics Collaboration)
        - github.com/astrostat
    - one of the lead developers of gammapy
    - github.com/adonath
- for poisson data you are always in the "low signal to noise" regime
    - you need to learn some data that is available a priori, e.g. "poisson statistics" of the data
- lira = "objective function extended by a log-prior term"
- LIRA = Low counts Image Reconstruction and Analysis
- implemented using pybind11

### J. Petabyte-scale ocean data analytics on staggered grids via the grid ufunc protocol in xGCM

- speakers: Thomas Nicholas, Julius Busecke, Ryan Abernathey
- LLC4320 --> global ocean MITgcm simulation
    - 1/48th degree horizontal spacing, hourly
    - lives on pangeo cloud storage
    - a single variable is 8.76 TB
- "`numpy` ufuncs" are kind of like "the kernel of the operation you want to perform"
- test coverage was crucial, since this poroject involved change almmost all of the internals
- "root task explosion" in Dask
    - if your graph starts with multiple independent "root" tasks that do something like load data, you can quickly excceed the available memory
- re-wrote xGCM and xhistogram to perform better at very large scale with Dask

### K. pyampute for data imputataion

- "amputation" is the opposite of "imputation"
    - imputation = filling in gaps
    - amputation = removing non-gaps
- epistemic uncertainty = "not enough data, knowable but not known"
- aleatoric uncertainty = "not knowable / stochastic"
- statistical uncertainty = variation
- systematic uncertainty = bias
- missingness types
    - missing completely at random
    - missing at random = "missingness is related to some other observed variable"
    - missing not at random = "missingness is related to some other variable, but you don't have data about it"
- `pyampute` allows you to introduce missing data in a controlled way
    - types of missingness
    - severity of missingness
- this talk used DeepNote
- you can add a "mechanism" describing which type of missingness should be used
    - e.g., "missing at random" with probability influenced by some other variable
- https://github.com/RianneSchouten/pyampute
- noted that this package has similar behavior to `mice::ampute()` iin the `{mice}` R package

### Lightning Talks

- Can a neural network trained on images of the physical world recogize cartoons?
    - twitter.com/DJCordhose
- "teaching signal processing to musicians with jupyterbook"
    - https://bit.ly/dstbook-scipy
    - librosa
- "jupyter kernels as a service"
    - https://conda.store
    - "conda environments for teams"
    - nbccondakernels
- "machine learning is a natural science"
    - Anthropic (interpretable ML B-corp)
- quantum in the cloud
    - microsoft
    - quantum computers operate at something like "10 milli-Kelvin"
    - thaat sounds cold
- [missed title]
    - speaker: Javier Luraschi
    - "I used to be an R user"
    - tensorflow.js in the browser
- Awesome HRR
    - HRR is "the best weather model we have in the U.S."
    - HRR is on AWS Public Data...as 4000+ GRIB2 files per day
    - Kerchunk + fsspect to convert all the HRR GRIB2 stuff into JSON
    - also using Jupyter, Dask, Zarray, Zarr, Holoviz
- data mapping: an auditing tool
    - 

### Misc notes

* Jim Pivarski mentioned that it's common in some fields to store data in histograms, using the Boost histogram object or the Python `hist` package
    - maybe LightGBM could be modified to allow creating a `Dataset` from such objects

## Day 2


### A. Python's Contribution to Astronomy and Major Space Missions

- a bunch of astronomy stuff did run on Solaris and still might
- Perry Greenfield + Rick White + John Hunter
    - introducing Python to astronomy
    - PyRAF, pyFITS, matplotlib
- `numeric` + `numarray` were combined to create `numpy`
- Hubble - majority of software written in C
- Webb - majority of the core software is written in Python, with C extensions
    - uses `astropy` extensively
    - instruments share common core code, complicatedd by "large number of observing modes"
- other packages:
    - ASDF (github.comm/asdf-format)
    - GWCS (github.com/spacetelescope/gwcs)
- astroquery
- Barbara A. Mikulski Archive for Space Telescopes (MAST)
- telescopes: Hubble, Webb, Roman
    - Webb: 114 TB of science data per year
        - 650 TB during the primary mission
    - Roman: STScl prooviddes science operations
        - generates 9 TB / day
        - STScI will provide a "data-local analysis environment in the cloud" for researchers to access this data
- Nancy Grace Roman Space Telescope launches in 2026
- Roman data is "non-proprietary and comes with no exclusive access limitations"
- open development
- there is no Python on Roman itself... but soome of the control is in javascript
- 

## Things to Google

- "advanced photon source"
- alibi explain (from seldon)
- aperture
- arc seconds
- Argonne + DOE "self-driving iaboratories"
- awkward array
- "beamline data" from APS
- colmena
- continuous curvature spline
- cubed
    - https://github.com/tomwhite/cubed
- force11.org/group/fairgroup
- foundry
    - github.com/MMLMI2-CSSI/foundry
    - ML-ready datasets
- funcx
- Hypothesis (property-based testing)
- jupyterbook
- LFortran
- librosa
- Li-ion
- materials genome initiative
- "mesoscale fronts" (re: ocean simulations)
- nanobind (https://github.com/wjakob/nanobind)
- `numpy.roll()`
- parsl
- `photutils`
- poisson statistics
- PyBaMMM
- pybind11
- PyRAF
- PyTables
- quantization
- richclick
- "serial x-ray crystallography"
- `typing.Annotated`
- vorticity & strain
- xarray
- xarray-beam
- xGCM
- xhistogram
- zarr
