# Open Data Science West (2015)

## Conference Details

Location: San Francisco, CA
Dates: 
URL: https://www.opendatascience.com/tag/odsc-west-2017/

## Speaker Notes

### Day 1

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
