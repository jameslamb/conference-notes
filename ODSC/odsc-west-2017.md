# Open Data Science West (2015)

## Conference Details

Location: San Francisco, CA
Dates: 
URL: https://www.opendatascience.com/tag/odsc-west-2017/

## Speaker Notes

## Day 1

**A. Keynote: Sheamus McGovern**

- ODSC is cool and stuff

**B. Keynote: Remus Lazar**

- Directory, Data science at IBM
- "many of the problems you face in your professional life are around finding and working with the right model"

**C. Keynote: DJ Patil**

- "our technology isn't revolutionary if everyone can't use it"
- made the point that 11.4 million Americans go through local jails every year and 95% don't go on to prison
- "your edge cases have names"

**D. Keynote: Igor Perisic**

- VP of Engineering at LinkedIn
- "The Deontology of data science"
- the math roots our our science:
    + Pascal - probability
    + Bayes - conditionaly probability
    + Gauss - normal distribution
- the compsci roots:
    + Alan Turing
    + Grace Hopper (we don't need to all code Assembly)
    + Don Knuth

**E. Wes McKinney - Shared Data Science Infrastructure**

- "data science wasn't even a thing when I started working on Pandas"
- when pandas started, using Python for statistics wasn't really a thing
- in open source, there's not a direct economic relationship with users and developers
    + the cost of bugs is basically reputation of private individuals
- "we've seen the data science community come together and start to collaborate on certain types of problems":
    + Jupyter (interactive, reproducible research)
- "everyone (regardless of framework) needs to read files"
- 

**I. Monetization Strategies for ML Engines**

- ANI = "artifical narrow intelligence"
- AGI = "artificial general intelligence"
- ASI = "artiificial super intelligence"
- This company is trying to build an "AI operating system"P
- Veritone aiWARE

**J. pomegranate: fast and flexible probabilistic modelling in python**

- Jacob Schreiber
- this guy is on the core development team for scikit-learn
- supported by eScience institute at University of Washington
- "pomegrante is more flexible, faster, intuitive to use, and can do it all in parallel"
- 6 main models:
    + probability distributions
    + GMMs
    + markov chains
    + hidden markov models
    + Bayes classifiers
    + bayesian networks
- you can create, for example, a Naive Bayes model that uses an HMM as a probability distribution
- "you can drag and drop any probability distribution"
- the takeaway:
    + you can get way faster performance by computing sufficient statistics (breaking things down into additive components)
- Bayesian networks:
    + people us them because they're very flexible to which data are there or missing
    + you can learn the dependency structure from data
- three ways to learn structure:
    + "search and score"
    + "constraint learning"
    + heuristics
- paper available on arxic:
    + https://arxiv.org/abs/1711.00137

**HEY. RStudio Discussion**

- "enterprise package management" beta coming in January-ish

## Day 2

**A. Differential Privacy**

- Bluecore
- Differentially private logistic regression:
    + "bolt-on method"

**B. Product managing Somewhat Intelligent Products that Work with Humans**

- Eugene Mandel, DS team at Directly
- "my favorite data science algorithm is division"
- using a "premortem"
    + before you start a project, imagine every way it could fail
    + then work to avoid that
- defensible ML products:
    + smarter models
    + proprietary data
    + better processes
- you have a sparse space of questions but dense clusters of answers
- word embeddings / word2vec can help here
- cleaning up dirty labels:
    + you should be tracking what % of your labels flip each time you talk to experts
    + you should focus on the things that your model calls a false positive and validate those (don't waste time validating obvious cases)

**C. How to combine subject matter expertise and data science to predict mechanical failures**

- SparkCognition
- "IoT space is very traditional"
    + lot of literature, papers on industrial domains like wind turbines
- what makes a subject matter expert:
    + SMEs understand context
    + SMEs know what to look for in specific settings
- Case study: cruise ship failure:
    + correlation does not mean causation
    + mentioned a case of alternator failures
    + SMEs can help to validate the features involved in predicting an anomaly
- SMEs do this:
    + help you to eliminate irrelevant features
- you have to care about operational state
    + expressed some skepticism about our ability to "cluster out state"
- wind turbine failure:
    + you need to understand transient behavior
    + like high vibration in some settings unrelated to a gearbox failure
- supervised approach:
    + focus on "failures"
    + predict failure risk
    + failure/normal data imbalances
    + but there's an issue...not enough examples of failures
- when working on turbines, they basically also decided to go with anomaly detection instead of a failure risk model
- they're basically re-inventined anomaly detection to try to solve this
- feature selection:
    + environmental:
        * ambient temp
        * wind speed
        * turbine rotor RPM (for misalignment)
        * load (account for generator efficiency / load correction)
    + seasonality:
        * generator NDE bearing and hydraulic oil temp
        * transformer and radiator temp
- they built a super complicated thing with CNN + LSTMs
- ways to reduce FPs
    - removing unnecessary sensors
    - checking for faulty sensors
    - examine maintence history
    - using persistence (x point in alarm zone continuously)
- next steps:
    + using transfer learning to take one model and apply it to other assets
- advice: don't jump right into the problem model-first

**D. Building cool stuff on AWS at Google**

- Chris Fregly
- PipelineAI
- old version of slides: https://www.slideshare.net/cfregly/high-performance-tensorflow-in-production-sydney-ml-ai-train-workshop-uai-conference
- you can auto-shift traffic to the "Winning model"
    + create three different models using 1 experiment
- you deploy a model and runtime as one image

```
pipeline predict-server-build --model-type=tensorflow --model-name=mnist --model-tag="b"
```

- you can run local load tests on your model
    + pipelineAI exposes a little GUI to tell you how long it takes to score new data
- "I always use port 6969 because I know nobo elses's stuff will be on there. Don't take that...it's mine now."
- at Netflix:
    + "I took down North America streaming for 2 hours"
    + I was responsible for pushing out new code...I thought this config parameter was in seconds, but it was milliseconds
- you can create experiments offline and online
    + once everything is Dockerized, you can create many alternate realities
- pipeline offers an "@log" decorator that lets you measure how different parts of your computation are impacting scoring time
- you could automatically capture the borderline cases and route them somewhere else:
    + for image recognition...post it to a Slack channel and give an ability for humans to validate the images
    + or put them on a "marginal cases" topic or whatever...bigger idea is you can create a dataset of bordline cases and then strategize on how to attack them
- at Netflix:
    + "don't worry about cost. The studio cost for Harold and Kumar go to Guantanamo Bay was more than you could spend on EC2s for 10 years"
- You could also get metrics like "cost per prediction" in real time (based on the type of instance you're running on)
- could automatically shift between Amazon, Google, Azure
- "if you're trying to use Docker with GPUs....don't"
    + there is a thing called "nvidia-docker" that wraps Docker. But blegh
- don't use Kubernetes + Docker + Tensorflow
- These CUDA libraries that NVIDIA ships are super closely tied to the kernel of the particular distribution of Linux you're running
- There's not technically a canonical "Ubuntu 16.04" image out there in the world. Amazon or whoever your cloud provider is will add some small patches
- Single precision vs. half precision:
    + advice: train your models at half precision (FP16)
- CUDA programming is "barbaric, but fun barbaric"
- NVIDIA can change the hardware whenever they want
- Parquet is columnar and made for analytics
- don't use `feed_dict` in TF in pduction
    + retrievs next batch after current batch is done. Single-threaded, synchronous
    + that means your CPUs / GPUs not fully utilized
- "Data scientists hate the term 'table' more than 'data frame', and data engineers dont care"
- if you don't shuffle inputs, your network will learn the order instead of things directly related to the problem
- Google web-trace framework:
    + http://google.github.io/tracing-framework
- "distributed Tensorflow has had a rocky road"
    + Google docs are way more up to date than Tensorflow.org
- advice: user a good cluser orchestrator (Kubernetes, Mesos)
- you can subscribe to people on Stack Overflow
    + and get a daily update of what people answer
- it's not uncommon to see Tensorflow choose a route through the the graph that consumes too much memory
- XLA Framework
    + "accelerated linear algebra" (XLA)
    + goals:
        * reduce reliance on custom operators
        * improve execution speed
        * improve memory usage
        * reduce mobile footprint
        * improve portability
    + this helps TF Stay flexible and performant
- AOT Compiler
    + "ahead-of-time compiler"
    + TensorFlow model serving:
        * AOT XLA Compiler and Graph Transform Tool
        * key components of TensorFLow serving
        * deploy optimized TF model
    + `tfcompile` binary (also built on XLA)
    + the TF runtime is 50MB
        * when you call `session.run()` you're pulling the entire thing in
        * lots of libraries you need for training but not at scoring time
        * `tfcompile` can take this all the way down to like 600kb

**A. "Shared Infrastructure for Data Science"**

- Speaker: Wes McKinney
- we still mostly process array data the way we did 30 years ago
- almost no code sharing across languages on problems like data frames
- "It used to be really hard to read CSVs"
- "maybe pandas is popular on Stack Overflow because it's so hard to use"
- "programming languages are user interfaces into computation"
- we can create a "shared data science runtime"
    - step 1: standard in-mem format for portable data frames
    - step 2: zero-copy interchange
    - step 3: access layers
    - step 4: flexible computation engine
        - zero-overhead UDFs
        - portable operator graphs
        - embeddable in larger systems
- Arrow as the primary format for DFs in memory
- goals:
    - O(1) random value access
    - zero-copy
    - flat and nested
- using ASF is an effective tool for commercial competitors to collaborate on open source stuff
- mentions:
    - Dremio
    - geomesa
    - SIMD
    - turbodbc
    - Ray project
- "pandas2" initiative
- optimization:
    - multicore scheduling
    - eliminatintion of temporaries
- "we can preserver the pandas API"

**B. Processing Unstructured Data**

- Meltwater
- big problem with web scraping is not one-time extraction
- "fully automated web extraction"
    - maybe you can use ML to write scrapters to recover from failure?
- Fairhair AI crawlers
- this guy claims they have a thing to turn any site into JSON
- serving off Elasticsearch (obvi)
- analytics layer with Spark, Hadoop
- offering "enrichment as a service"
- using "Snorkel" to generate training data

**C. Monotonicity**

- speaker: Maya Gupta
- when you know about monotonic relationships, you can enforce them
- idea: enforcing monotonicity as a form of regularization
- tensforflow Latticepackage
- semantic regularizers:
    - Laplacian
    - Tarsion (suppress nonlinearity)
- a small class of monotonic functions can be expressed as a neural net
- a "Lattice" is an interpolated lookup table
- Lattices are linear on a fixed nonlinear transform of X
- printers use interpolated lookup tables for color management
- tarsion regularizer = make stuff more linear
- "calibrated linear model"
    - automatically learn best transformation
- monotonicity helps with generalization to new data


## Things to Google

- mxnet
- ONNX
- GLUON
- pomegranate
- Chow-Liu trees
- Snorkel (https://github.com/HazyResearch/snorkel)
- TensorRT
- Istio
- Bandit
- http://google.github.io/tracing-framework
- Spark Tungsten
