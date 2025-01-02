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
- transformers and pipelines now support `get_feature_names_out()` to extract feature names

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
    - "a gamma ray and x-ray astronomer, working at Harvard Smithsonian in Boston"
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

- Can a neural network trained on images of the physical world recognize cartoons?
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
- pandas
    - pandas issue #7307 (open from 2014)
    - pandas only supports timestamps from 1678 AD to 2262 AD
    - this is not that fun if you are doing, for example, paleoclimatology
    - `pandaas` 2.0 wiill support non-nanosecond resolutions for datetime64 and timedelta64 dtypes
    - with second resolution, you can represent hundreds of billions of years in the past and present

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

### B. Plenary / tools

- jupyterlab
    - real-time collaboration is available as a beta feature in jupyterlab 3.0
- 2i2c
    - a non-profit which provides Jupyter, Dask, RStudio to non-profits
- xarray
    - joe hamman
    - `xarray` is for n-dimensional arrays
    - "nummPy with labels" or "n-dimensional pandas"
    - created a roadmap at scipy 2021 and have been workiing through it
- scikit-image
    - SIFT feature matching ("came out of patent recently")
    - Scale Invariant Featuure Transform
    - "perceptual blur metric"
    - they're now providing Apple ARM64 wheels
    - adding support for Dask, CuPy backend
- metPy
    - Python tools for meteoroloogy
    - added support for Dask
- sympy
    - a Python library for doing "symbolic mathematics"
    - adding Jax support
    - swiitched to Sphinx "Furo" theme
- "numpy contributor experience lead"
    -  Inessa Pawson
    - numpy and a few others got a Chan-Zuckerberg EOSS Grant
- networkx
    - v3.0 coming this fall
    - got a Chan-Zuckerberg EOSS grant
    - swapping in some linear algebra approaches to some graph algorithms (including GraphBLAS)
- Journal of Open Source Software
    - publishing "aaround 1 paper a day"
    - a journal for publishing open source sooftware packages

### C. Human-Friendly, Production-Ready Data Science with Metaflow

- "many of the machine-related problems in ML have gotten easier...it's the people problems that are really challenging now"
- all projects leverage 3rd party libraries... Netflix wanted to be "relatively unopinionated about which frameworks are used"
    - "we wanted to be opinionated about the infrastructure stack without putting any restrictions on data scientists' framework choices"
- Netflix used:
    - Trino
    - Spark
    - Snowflake
- Netflix had its own fleet of GPUUs to deal with cloud availability limitations
- even within one company, there isn't a canonical ML stack
- he showed that famous "how much data scientist cares" vs. "how much infrastructure is needed" graphic
- metaflow comes with a Python client library for launchinng jobs but also for interactively inspecting their state
- you just slap operators on your code to tell stuff to run on other infrastructure

```python
class MyFlow(FlowSpec)

    @resources(memory=128000)
    @step
    def start(self)
```

## D. Awkward Packaging: building Scikit-HEP

- speaker: Henry Schreiner
- PyROOT not not very Pythonic...
    - for example, in Python you have to preallocate memory, then fill it up
- by 2015, "you could do a lot of high-energy physics in the Python stack"
    - and that included using these ROOT files
- dealing with "jagged" data was a problem
- `uproot` was a ROOT file reader + writer, and installing it was as easy as `pip install uproot`
- awkward array was ddeveloped to support `uproot`
    - "jagged arrays", where you have a variable nuumber of values in each "row"
    - originally HEP focused, but nnow more general
    - this was first written in pure Python, but now has some compiled code in it
- `pybind11`
    - preferred over Cython / SWIG for `awkward` and `uproot`
- building redistributable wheels is tough
    - pypy?
    - musllinux?
    - ARM architecture? PPC architecture?
    - develwheel, auditwheel, delocate
- could use `azure-wheel-helpers` to build redistributable wheels
    - https://iscinumpy.dev/categories/azure-devops
    - tied only to Azure DevOps, small number of users
- tried `cibuildwheel` next
    - not tied to any one CI system
    - large number of users
    - sciikit-HEP made a bunch of contributions
    - PEP 517 + 518
    - scikit-HEP helped get `cibuildwheel` get into the Python Packagiing Authority (PyPA)
- protocols
    - `boost-histogram`
    - `mplhelp`
    - `upfroot`
    - created a "static protocol" called `UHI`
- using `typing.Protocol` might be preferable to `abc` because it doesn't require a runtime ddependency
- `uproot-browser` for viewing histograms
- linters
    - YesQA
    - PyCln
    - check-manifest
    - PyUpgrade
    - PyGrep hooks
    - clang-format
- scikit-build
- this project is interested in adding CMake support to support WebAssembly

### F. Simultaneous Demodulation of Multiple FM Stations

- @luigifcruz
- SDR = "a USB stick that can receive radio waves"
- you can use a GPU to do this demodulation
- U.S. radio uses a different "de-emphasis" than every other country in the world
- FM, WBFM, MFM
    - WBFM = "wide-band FM"
- talked about a case where `scipy` was casting to float64  automatically, which was leading to some unnecessary overhead
- "a DSP program is a chain of discrete functions sharing vectors of data"
- `scipy.signal.resample`
- damn this guy even put his HAM radio callsign up (PU2SPY)

### G. Python for Global Applications - Teaching scientific Python in context to law and diplomacy students

- speaker: Dr. Anna Haensch, Dr. Karin Knudson (tuft)
- created an "Introduction to Data Science" ccourse for law students at Tufts
- included "weapons of math destruction" and "how charts lie" in the course
- a lot of students said they had "fears" and "concerns" about programming
- "leverage existing strengths to enhance student ownership"
    - tried to get them comfortable by letting them work on problems they cared about
- used colab + jupyter + conda
- "Getting and Cleaning Data" --> "Visualizing Data and Communicating Findings" --> "Moddeling Data"
- https://karink520.github.io/data-science-for-global-applications

### H. Sampling in scipy

- scipy has: statistics, optimizatiion, interpolatiion, integration
- `dist.ppf()`
    - sample from a custom distribution
- see "autommatic random variate generateion in Python" in the proceedings
- C library `UNU.RAN`... scipy.stats.ssampling --> generate variates from non-standard distributions
- dpdf = "derivative oof the probability density funcctiion"
- discrete distributions
    - `DiscreteAliasUrn`
    - `DisccreteGuideTable`
- quasi-monte carlo
    - deterministic method for sampling
    - not IID
- brought up the interesting point that you might care more about how truly "random" sampling is if you are relying on that randomness as a security mechanism
- quasi monte-carlo is a way to sample any distribution
- discussion about "true random numbers", even some methodsd based on the temperature of the system

### I. Using Python to Protect Voting Rights

- speakers: Karin Knudson, Chanel Richhardson
- Tufts redistricting lab
- "the Gingles factors"
    - factors that you have to show evidence of to make a voting rights acts case
    - 1 - is the minority group large enough and geographically centered enough to be a majority within a district?
    - 2 - do minority voters vote cohesively?
    - 3 - does majority group vote in a bloc preventing minority voters from electing their preferred candidate?
- the U.S. uses secret ballots, so you can't directly measure a breakdown of votes by characteristic like race or gender
- you can cross-reference demographic data from the census and voting records summarized at a precinct level
    - bounded by the total number of registered voters and ballots cast
- "ecological regression"
    - fraction of vote for a candidate depends linearly on the fraction of the population in that group
- more recently, Bayesian hierarchical model is used for EI ("ecological inference")
- they use PyMC + Jax
- PyMC = "efficient markov chain monte carlo sampling"
- arviz
- PyEI was recently used for a case in Texas about "are non-white votes voting as a bloc?"
- there is a nother every-5-years survey called the ACS
    - similar to the census
    - lines up with voting years
- this work does help detect how representative a map is of the underlying population

### J. Lightning Talks

- building the least stable virtual env
    - thomas caswell, matplotlib maintainer
    - github.com/tacaswell
    - well-run libraries LOVE bug reports that we broke downstream projects on main
    - `pip install --pre`
    - you can also get release candidates from conda-forge
    - it's possible to publish nightly wheels to PyPI
    - github.com/tacaswell/build_the_world
        - buch oof shell scripts that builds CPython all the way up to like `pandas`
    - `pip install --no-build-isolation`
- cadCAD: modeling library for generalized dynamical systems
    - "compleze adaptive dynaimics computer aided design"
    - "tools like Simulink, Stella, Moddelica aren't as intuitively extensible"
- OpenTeams global
    - founded by travis oliphant
    - "global network of open source developers"
    - "we're going to become the LinkedIn for open source developers"
- container canary
    - jacob tomlinson
    - talked about making a change to RAPIDS image which broke an nvidia service
    - (!!!) github.com/NVIDDIA/container-canary
        - a testing framework for container images!!
- opart - a Python tool for optimal art curation
    - talked about how the art collection at tufts wasn't representative of the student population
    - schelling's model of segregatiion
        - "even mild in-group preferences lead to segregation"
    - a super over-engineered library for making decisions about where oon campus what types of art should be
- 10-ish years of SciPy proceedings
    - dillon niederhut
    - scipy proceedings has gotten closer and closer to only have 1 reviewer per paper
- time series downsampling for visualizations
    - Delaina Moore, data scientist @ Chevron
    - "Largest Triangle Three Bucket" (LTOB) algorithm
    - "Downsampling time series for visual representation" by Sveinn Steinarsson
- JWST data with jdaviz
    - `Jdaviz` ddevelopedd by `STScI`
    - "space telescope science institute"
- spiral of silence
    - "people tend to not express any of their characteristic that is different from the group"
    - "stop executing javascript"
    - `chmod a-x the_web`

## Day 3

### A. Introduction

- back in the day, "Hubble was committed to Python even when Python wasn't cool"
- "the first image of a black hole I saw was through matplotlib"
- SciPy 2023 will be transitionedd to NumFOCUS

### B. SciPy in Climate Science

- Peter Kalmus (JPL)
- LIGO search for gravitational waves
- AIRs = hyperspectral infrared sounder on Aqua satellite
    - usedd to measure atmospheric water pressure
- `SHARPpy` to calculate thermodynamic indices
- multivariable fire prediction - MFIRE
    - 2m air temperature (NST, from dataa fusion)
    - vapor pressure deficit (VPD, from data fusion)
    - surface soil moisture percentile (GRACE)
    - root zone soil moisture percentile (GRACE)
    - land cover type (USGS)
- "vapor pressure deficit" = "how hot and dry is it around a leaf, which determines how likely it is that moisture will want to leave the leaf"
- ecological projection
    - coral (increasing ocean heat)
    - once the ocean water gets hotter than what the ccoral is used to, coral will "bleach" and start producing toxins
- increasing extreme humid heat
    - the poorest people tend to live in hotter neighborhoods
    - less trees, more pavement
- "the conda package manager used to work great, then it stopped a few years ago"
- list of packages mentioned
    - seaborn
    - scikit-image
    - tensorfloow
    - keras
- "we are getting more in Julia"
- "99% of corals will probably die before the middle of the century"
- "this is really scary sstuff...and I'm affected emotionally"
    - "a lot of climate scientists are freaking out and we're not sure as a professional group how to have an honest conversation about the emotional impact of this"

### C. conda-forge (tools plenary)

- speaker: wolf
- "the largest channel for the conda and mamba package managers"
- `mamba-org/boa`

### D. numpy (tools plenary)

- new in v1.23.0 = "a much faster `load_txt()`"
- grants from Chan Zuckerberg initiative
- updated docs to use jupyterlite

### E. matplotlib (tools plenary)

- Chan Zuckerberg grant, NASA ROSES grant
- "moved documentation from GitHub pages to Digital Ocean"
- a new trove classifier: `Framework :: Matplotlib`
- `subplot_mosaic()` = arrange multiple plots
- you can make slides in matplotlib

### F. Mayavi: 3D visualization (tools plenary)

- has been around for 20+ years
- enables you to create 3D visualizations and UIs

### G. Napari (tools plenary)

- `napari` proovides GUI access to the scientific Python stack
- viewer and annotation tool

### H. sunpy / PyHC (tools plenary)

- `sunpy` is for solar physics data
    - extends `astropy`
- https://heliopython.org
- `PyHC` is a collaboration between developers for heliiophysics projects

### I. zarr (tools plenary)

- speaker: John Kirkham
- there's a new `zarr` logo
- implementation in Python, Julia, Rust, C++
- https://zarr.dev/zeps

### J. pangeo (tools plenary)

- https://pangeo.io
- Xbatcher
- rechunker

### K. prefect

- speaker: kevin khoo
- `@task(cache_key_fun, cache_expiration)`
    - cache task results based on some function
- awesome live demo
- prefect "task library" became "prefect collections catalog" in prefect 2.0
- e.g. `prefect-slack`, `prefect-twitter`
- `prefect deployment create`
    - Prefect has a "deployments" concept whiich is like a flow + scheduling
- Flyte is k8s-native, and assumes that everything is in containers
    - "we have a lot of people who learn prefect soon after they learn Python"
    - Dagster, Flyte are more opinionated than Prefect

### L. Pragmatic Panel: Build and Deploy Complex Data-Driven WebApps

- speaker: Kim Pevey (Quansight)
- `panel` is "part of the holoviz stack"
- voila, holoviz
- QHub (aka Nebari)
    - "an opionated jupyterhub deployment"
- in panel, you can choose a configurable "backend" for widgets
- `pn.state.location.sync()`
    - programmatically update the state of a visual element
- Panel creates interactive visualizatioons, and you can then run Python code to update their state :mind_blown:
- panel state give you a bunch of options to modify the visual state of apps programmatically

### M. How do you test data workflows?

- spaker: Paul Anzel (https://www.linkedin.com/in/paulanzel/)
- generating random data:
    - `faker`
    - Mockaroo, GenerateData
- static analysis
    - test your code wiithout running it
    - `check-yaml` = test for syntactically-valid yaml
    - `check-toml` = test for syntactically-valid tooml
    - `check-jsonschema` = check if a YAML file matches a specific schema (defined in JSON)
    - `sqlfluff` = parsing and linting SQL
- this talk was like "everythhing you should know about testing"
- `bandit` (security static analysis)
- `pip-audit`

### N. pybind11 and building C extensions panel

- feedstocck maintainers can talk to conda-forge about archiving things
- PEP 517, 518
- Henryy Schreiner: "I'm a really big fan of type hints"
- what about type hints for like "this is a 2D array of floats"?
    - "there is a PEP that landed for Python 3.11 for that"
    - PEP 646
- some discussions about how hard it is to support other architectures
    - M1 Macs, yeah, but also Windows-on-ARM
    - you can do cross-compilation, sure, but how do you test it
- "it might make it better to remove support for lists of lists in `numpy`"
    - "we should probably stop just converting everything that could be a `numpy` array to array"
    - libraries should stop supporting nested lists as "array-like"

### O. Lightning talks

- scipy diversity statistics
    - 992 attendees, 32 countries
    - volunteer: https://biit.ly/2UR8SoR
    - scipy@enthought.ccom
- introduction to lockfiles
    - matt feickert
    - barba group
    - matt is part of a team focused on ensuring that work done at the LHC at CERN is reproducibe 5-10 yeaars in the future
    - `pip-compile --generate-hashes --output-file requirements.lock`
    - `pip-secure-install`
    - Brett Cannon's iidea about secure installs for applications:
        - `pip install --no-deps --require-hashes --only-binary ':all:'`
    - `pip install --no-deps --require-hashes --only-binary ':all:' requirements.lock`
- how to organize SciPyConf Mars edition
    - Lambert's problem: "I want to get from point A to point B in a fixed amount of time"
    - `lamberthub` = solving this problem in Python
    - "porkchop plots" in `poliastro`
    - `porkchop.plotting.porkchop.PorkChopPlotter`
- tethys platform
    - a Python CLI that makes web apps
    - tethysplatform.org
- keck data
    - `pyKOA` for the "keck observability data"
- conda
    - cheng H. Lee (works at Anaconda, conda core maintainer)
    - plugged the `libmamba` solver into `conda`
    - `conda create --experimental-solver=libmamba`  (and soon that flag will go away)
    - faster conda-forge, bioconda publishing
    - CEP ("enhancement proposal") github.com/conda-incubator/ceps
    - conda is starting to publish release schedules, like "what versions of conda are supported, what version of CPython"
    - conda's governance is changing to "prevent capture"
    - they've applied to be a NumFOCUS-sponsored project
    - therre are conda sprints tomorrow
- pyplot
    - `import hvplot.pandas; df.hvplot()`
    - hvplot.holoviz.org
- sunpy
    - "a while ago I decided I hated threads, and wrote an async file downloader"
    - "wrote a different library using `asyncio` to do download and read files"
    - presents a synchronous API, but uses `asyncio` to handle parallelism
    - `parfive`
- korbit
    - andy terrel
- mpl-interactions
    - a package providing an "interactive matplotlib backend"
- linking lincoln
    - "it's off the chain"
    - IPUMS - census data from University of Minnesota
    - `hlink` = record linkage based on name, age, etc.

## Things to Google

- "advanced photon source"
- alibi explain (from seldon)
- aperture
- arc seconds
- Argonne + DOE "self-driving iaboratories"
- arvic (diagnosticis for sampling)
- auditwhheel
- awkward array
- `bandit` (SAST)
- barba group reproducibility syllabus
- "beamline data" from APS
- colmena
- `conda-lock`
- continuous curvature spline
- cubed
    - https://github.com/tomwhite/cubed
- delocate (Python package building)
- develwheel
- discrepancy metric (in the context of random sampling)
- "envelope detection" (FM radio)
- FFT (fast fourier transform)
- fisk distribution
- flox
- force11.org/group/fairgroup
- foundry
    - github.com/MMLMI2-CSSI/foundry
    - ML-ready datasets
- funcx
- GraphBLAS
- hilbert functions
- Hypothesis (property-based testing)
- `intake` (memtnioned as a pyplot input similar to dask)
- jax
- jupyterbook
- jupyterlite (jupyterlab distribution that runs in the browser)
- KDDE (kernel density estimate)
- LHS (latin hypercube sampling)
- Largest Triangle 3-bucket algorithm (for downsampling data for visualization)
- Lambert's problem
- LFortran
- librosa
- Li-ion
- materials genome initiative
- "mesoscale fronts" (re: ocean simulations)
- metropolis-hastings sampling
- mono vs. stereo output
- nanobind (https://github.com/wjakob/nanobind)
- `nox`
- `numpy.roll()`
- Panel (holoviz)
- pangeo forge
- `parfive` (parallel downloads)
- parsl
- pdm (like pip-tools)
- `photutils`
- pip-audit
- porkcchop plot
- poisson statistics
- PyBaMMM
- pybind11
- PyEI ()
- PyMC
- PyRAF
- PySide6
- PyTables
- quantization
- rechunker
- richclick
- ring buffer
- SAST static analysis (security issues)
- scipy signal
- "serial x-ray crystallography"
- SHARPpy
- sobol sampling
- `sqlfluff`
- streamlit
- `typing.Annotated`
- uarray
- UNU.RAN
- UUHI
- vorticity & strain
- VTK-widgets
- xarray
- xarray-beam
- Xbatcher
- xGCM
- xhistogram
- YAML bombs
- zarr
